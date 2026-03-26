# Claude ASO — App Store Optimization for Claude Code, Codex & Co.

Comprehensive App Store Optimization skill for Claude Code, Codex, Cursor, and any AI agent that supports skills. Analyzes iOS App Store and Google Play listings using parallel subagents across 7 categories, producing an ASO Health Score (0-100) and prioritized action plan.

Inspired by [AgriciDaniel/claude-seo](https://github.com/AgriciDaniel/claude-seo) — adapted from SEO website analysis to ASO mobile app optimization with the same parallel subagent architecture.

## Features

- **Local-first**: run `/aso audit` inside your app project — auto-detects Fastlane metadata, Xcode, or Gradle and audits pre-submission metadata
- **Remote audit**: run `/aso audit <app-id>` to audit any live listing or competitor
- **13 specialized sub-skills**: keywords, metadata, visuals, reviews, competitors, localization, A/B testing, technical, conversion, planning, launch, seasonal
- **9 parallel subagents**: full audit spawns agents simultaneously for fast analysis
- **Platform-aware**: auto-detects iOS vs Android, applies correct rules (character limits, indexing behavior, A/B testing capabilities)
- **Quality gates**: prevents bad recommendations (no keyword stuffing, respects char limits, iOS description not indexed)
- **Extension system**: optional AppTweak and App Store Connect API integrations

## Quick Start

The easiest way: point your AI agent at this repo and ask it to set it up.

```
Install https://github.com/felixgraeber/claude-aso and run an ASO audit on my app
```

Or install manually:

```bash
git clone https://github.com/felixgraeber/claude-aso.git
cd claude-aso
bash install.sh
```

Then in Claude Code / Codex / Cursor:

```
/aso audit                      # Auto-detect local project metadata
/aso audit id284882215          # Audit live iOS listing (Facebook)
/aso audit com.whatsapp         # Audit live Android listing
/aso audit --compare id123      # Compare local metadata vs live listing
/aso keywords "habit tracker"   # Keyword research
/aso metadata                   # Optimize local metadata
```

## Commands

| Command | Description |
|---------|-------------|
| `/aso audit` | Auto-detect local project and audit its metadata |
| `/aso audit <app-id>` | Audit a live listing by app ID or store URL |
| `/aso audit --compare <app-id>` | Compare local metadata vs live listing |
| `/aso keywords <seeds>` | Keyword research and placement strategy |
| `/aso metadata` | Optimize local metadata (or remote with app ID) |
| `/aso visuals` | Analyze local screenshots (or remote with app ID) |
| `/aso reviews <app-id>` | Review sentiment and response strategy |
| `/aso competitors <app-id>` | Competitor gap analysis |
| `/aso localization` | Audit local locale coverage |
| `/aso ab-testing <app-id>` | A/B test design |
| `/aso technical <app-id>` | Technical health check |
| `/aso conversion <app-id>` | Conversion rate optimization |
| `/aso plan <category>` | Strategic ASO roadmap |
| `/aso launch` | Pre-launch checklist using local project state |
| `/aso seasonal <app-id>` | Seasonal keyword calendar |

## Local Project Detection

When no app ID is provided, `detect_project.py` scans the working directory:

| Source | Detected | Files |
|--------|----------|-------|
| Fastlane iOS | Name, subtitle, keywords, description per locale | `fastlane/metadata/{locale}/*.txt` |
| Fastlane Android | Title, short/full description per locale | `fastlane/metadata/android/{locale}/*.txt` |
| Xcode | Bundle ID, app name | `*.xcodeproj`, `Info.plist` |
| Gradle | Application ID, app name | `app/build.gradle`, `AndroidManifest.xml` |

Fastlane metadata provides the richest data (all store fields, all locales). Xcode/Gradle provide only identifiers — the tool will offer to fetch the live listing for a full audit.

## Architecture

```
aso/SKILL.md              Main orchestrator (entry point)
skills/aso-*/SKILL.md     13 specialized sub-skills
agents/aso-*.md           9 parallel subagents
references/*.md           Platform specs, quality gates
scripts/*.py              Python utilities (fetch, parse, validate)
extensions/               Optional API integrations
```

## Scoring

The audit produces a weighted ASO Health Score:

| Category | Weight |
|----------|--------|
| Keywords | 20% |
| Metadata | 20% |
| Visuals | 15% |
| Reviews | 15% |
| Competitive | 10% |
| Technical | 10% |
| Conversion | 10% |

## Extensions

| Extension | Purpose | Requires |
|-----------|---------|----------|
| AppTweak | Live keyword data, rankings, competitors | API key ($69+/mo) |
| App Store Connect | Direct Apple API for metadata and reviews | Developer account |

## Requirements

- Python 3.12+
- An AI agent that supports skills: [Claude Code](https://docs.anthropic.com/en/docs/claude-code), [Codex](https://openai.com/index/introducing-codex/), [Cursor](https://cursor.com), or any Agent Skills-compatible tool
- Optional: Playwright for visual analysis

## License

MIT
