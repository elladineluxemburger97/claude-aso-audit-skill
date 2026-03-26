---
name: aso-audit
description: >
  Full app listing audit with parallel subagent delegation. Scores listing
  across 7 categories (0-100), flags problems, generates prioritized action plan.
  Works in local mode (auto-detect Fastlane/Xcode/Gradle metadata) or remote
  mode (fetch live listing by app ID). Triggers on: "audit", "full ASO check",
  "analyze my app", "listing health check".
user-invokable: true
argument-hint: "[app-id-or-url] [--country CODE]"
---

# ASO Audit — Full Listing Analysis

Comprehensive app listing audit that spawns 7-9 specialized subagents in parallel.

## Modes

| Mode | Trigger | Data Source |
|------|---------|-------------|
| **Local** | `/aso audit` (no args) | Fastlane metadata, Xcode project, Gradle project |
| **Remote** | `/aso audit <app-id>` | Live App Store / Google Play listing |
| **Compare** | `/aso audit --compare <app-id>` | Both local + remote, shows diff |

## Process

### Step 1: Get Metadata (sequential)

**If no app ID provided (local mode):**
```bash
uv run python scripts/detect_project.py --json
```
This scans the working directory for Fastlane metadata (`fastlane/metadata/`), Xcode project (`.xcodeproj`), or Gradle project (`app/build.gradle`). If Fastlane metadata is found, all store fields are available. If only Xcode/Gradle is found, extract the app/bundle ID and offer to fetch the live listing.

**If app ID provided (remote mode):**
```bash
uv run python scripts/fetch_listing.py <app-id> --country us --json
```
For Android, also pipe through `parse_listing.py`.

**If --compare flag (compare mode):**
Run both detect_project.py AND fetch_listing.py, then diff the results.

### Step 2: Platform & Category Detection (sequential)
- Detect iOS vs Android from project type or app ID format
- Classify category from listing metadata (Gaming, SaaS, Health, E-commerce, Social, Fintech, Other)
- Load category-specific benchmarks

### Step 3: Parallel Subagent Dispatch

**IMPORTANT: Run ALL agents in FOREGROUND (not background).** Launch them all in a single message with multiple Agent tool calls so they run in parallel, but do NOT use `run_in_background`. This ensures you have all results before proceeding to Step 4. Do NOT output anything to the user between launching agents and presenting the final report.

Spawn ALL of these agents simultaneously using the Agent tool:

| Agent | Input | Focus |
|-------|-------|-------|
| aso-keywords | listing JSON | Keyword coverage in title, subtitle/short desc, keywords field, description |
| aso-metadata | listing JSON | Field quality, character limits, utilization, keyword placement |
| aso-visuals | listing JSON | Screenshot count, narrative flow, icon, preview video |
| aso-reviews | listing JSON | Rating, sentiment distribution, themes, response rate |
| aso-competitors | listing JSON + category | Top 5 competitors, keyword gaps, metadata comparison |
| aso-technical | listing JSON | App size, update recency, stability, category fit |
| aso-conversion | listing JSON | First-impression elements, screenshot narrative, CRO |

Conditional agents (spawn if relevant):
| aso-localization | listing JSON | If app supports >1 locale |

Each agent returns: `{ score: 0-100, findings: [...], recommendations: [...] }`

### Step 4: Score Aggregation (sequential)

Once ALL agents have returned, calculate the weighted score:

| Category | Weight | Source Agent |
|----------|--------|-------------|
| Keyword Optimization | 20% | aso-keywords |
| Metadata Quality | 20% | aso-metadata |
| Visual Assets | 15% | aso-visuals |
| Reviews & Ratings | 15% | aso-reviews |
| Competitive Position | 10% | aso-competitors |
| Technical Health | 10% | aso-technical |
| Conversion Signals | 10% | aso-conversion |

**ASO Health Score** = weighted average, rounded to integer.

### Step 5: Report Generation (sequential)

Generate two files in the current directory:

**ASO-AUDIT-REPORT.md** — detailed findings per category.

**ASO-ACTION-PLAN.md** — prioritized checklist (Critical > High > Medium > Low).

### Step 6: Final Summary (CRITICAL — this is what the user sees)

After writing both report files, output a clean, well-formatted summary to the user. This is the most important part of the audit — it must be the LAST thing shown and must be visually clear.

**Format the final output EXACTLY like this:**

```
## ASO Audit: [App Name]

**Score: XX/100** | Platform: [iOS/Android] | Category: [category]

### Score Breakdown

| Category           | Score | Status |
|--------------------|-------|--------|
| Keywords           | XX    | [emoji-free status word] |
| Metadata           | XX    | ... |
| Visual Assets      | XX    | ... |
| Reviews & Ratings  | XX    | ... |
| Competitive        | XX    | ... |
| Technical          | XX    | ... |
| Conversion         | XX    | ... |

### Top Issues

1. **[Issue title]** — [one-line description with specific fix]
2. **[Issue title]** — [one-line description with specific fix]
3. **[Issue title]** — [one-line description with specific fix]

### Quick Wins (< 30 min)

- [Action] — [expected impact]
- [Action] — [expected impact]
- [Action] — [expected impact]

Full report: `ASO-AUDIT-REPORT.md` | Action plan: `ASO-ACTION-PLAN.md`
```

**Rules for the final summary:**
- Keep it SHORT — max 40 lines. The detail is in the files.
- Top Issues: exactly 3, the most impactful ones.
- Quick Wins: 3-5 items, things achievable in under 30 minutes each.
- Status words: use "Excellent", "Good", "Needs Work", "Poor", "Critical" (no emojis).
- End with file paths so the user knows where to find the full detail.
- Do NOT repeat the full findings — that's what the report files are for.

## Available Tools
Read, Bash, Write, Glob, Grep, WebFetch, Agent

## Error Handling
- App not found → report error, suggest checking ID format
- Partial data → run available agents, note missing data in report
- Agent timeout → report partial results, mark category as "incomplete"
