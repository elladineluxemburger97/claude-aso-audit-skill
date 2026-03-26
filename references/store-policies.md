# App Store & Google Play Policy Reference

Enforcement rules for ASO compliance checking. Organized by violation type.
Every rule includes the specific guideline reference for citing in reports.

## Title / App Name Restrictions

### Apple App Store
| Rule | Reference | Detail |
|------|-----------|--------|
| Max 30 characters | 2.3.7 | Must be unique |
| No trademarked terms | 2.3.7 | Unless you own the trademark |
| No popular app names | 2.3.7 | e.g., "like Instagram" |
| No pricing info | 2.3.7 | e.g., "Free", "$0.99" |
| No irrelevant phrases | 2.3.7 | Every word must relate to app function |
| No other platform names | 2.3.10 | e.g., "Android", "Google Play" |
| No competitor brand names | 4.1(c) | Strengthened Nov 2025: no competitor icons/brands/names |

### Google Play
| Rule | Reference | Detail |
|------|-----------|--------|
| Max 30 characters | Metadata Policy | Changed from 50 to 30 in 2023 |
| No emojis or emoticons | Metadata Policy | Strictly prohibited in title |
| No ALL CAPS | Metadata Policy | Unless part of registered brand name |
| No special character abuse | Metadata Policy | No repeated symbols |
| Banned words in title | Metadata Policy | See banned words list below |
| No performance indicators | Metadata Policy | "#1", "best", "top" |
| No ranking claims | Metadata Policy | "most downloaded", "award-winning" |
| No pricing/promotional claims | Metadata Policy | "free", "no ads", "sale", "discount" |
| No call-to-actions | Metadata Policy | "download now", "install now", "update now", "play now", "try now" |

## Description Restrictions

### Apple App Store (Description NOT indexed — but still reviewed for policy)
| Rule | Reference | Detail |
|------|-----------|--------|
| Max 4,000 characters | 2.3 | |
| No misleading claims | 2.3.1 | About features app doesn't have |
| Must disclose IAP | 2.3.2 | If featured items require purchase |
| No pricing information | 2.3.7 | In metadata fields |
| No other platform references | 2.3.10 | No "also on Android" |
| No competitor brand names | 4.1(c) | No "better than [competitor]" |

### Google Play
| Rule | Reference | Detail |
|------|-----------|--------|
| Max 4,000 characters (full) | Metadata Policy | |
| Max 80 characters (short) | Metadata Policy | |
| No ALL CAPS abuse | Metadata Policy | In short description |
| No emojis in short description | Metadata Policy | Emojis allowed only in full description |
| No user testimonials | Metadata Policy | "Users say..." or quoted reviews |
| No ratings claims | Metadata Policy | "4.9 stars", "top rated" |
| No performance stats | Metadata Policy | "million downloads", "fastest growing" |
| No pricing/promotional info | Metadata Policy | "$X off", "free trial", "limited time" |
| No call-to-actions | Metadata Policy | "download now", "install today" |
| No competitor brand names | IP Policy | |
| No misleading functionality claims | Deceptive Behavior | Must match actual app behavior |
| No repetitive keywords | Spam Policy | Keyword stuffing penalized |

## Keyword & Metadata Spam

### Apple App Store
| Rule | Reference | Detail |
|------|-----------|--------|
| No trademarked terms as keywords | 2.3.7 | Apple may modify keywords at any time |
| No competitor app names | 2.3.7 | "alternative to [app]" in keywords |
| No irrelevant phrases | 2.3.7 | Keywords must match app functionality |
| Keyword spam = program removal | 4.3 | Apple Developer Program expulsion |

### Google Play
| Rule | Reference | Detail |
|------|-----------|--------|
| No repetitive keywords | Spam Policy | Triggers algorithmic penalty |
| No keyword stuffing | Metadata Policy | Unnatural density flagged |
| No competitor names | IP Policy | Trademark infringement → suspension |
| No misleading keywords | Deceptive Behavior | Must reflect actual features |
| Recommended density ~3% max | Best Practice | Higher triggers spam detection |

## Screenshot & Visual Asset Requirements

### Apple App Store
| Rule | Reference | Detail |
|------|-----------|--------|
| Must show app in use | 2.3.3 | Not splash screens, login pages, or title art |
| Must reflect actual experience | 2.3.3 | No fake UI or non-existent features |
| 4+ age rating for visuals | 2.3.8 | Even if app is rated higher |
| Must have rights to all content | 2.3.9 | Use fictional account info |
| No other platform imagery | 2.3.10 | No Android screenshots |

### Google Play
| Rule | Reference | Detail |
|------|-----------|--------|
| Must show actual app UI | Metadata Policy | No promotional graphics without app UI |
| No device mockups | Metadata Policy | No "screenshot inception" |
| No promotional text in screenshots | Metadata Policy | No "#1", "Best", "Top", "Sale" |
| No call-to-actions | Metadata Policy | No "download now" overlays |
| No ranking claims | Metadata Policy | No "million downloads" |
| No masking/transparent backgrounds | Metadata Policy | |
| Min 320px, max 8000px | Technical Req | 16:9 or 9:16 aspect ratio |
| Max 8 per device type | Technical Req | |
| No misleading visual elements | Deceptive Behavior | |

## Pricing & IAP Disclosure

### Apple App Store
| Rule | Reference | Detail |
|------|-----------|--------|
| Disclose IAP in description | 2.3.2 | Screenshots and previews too |
| "Free" requires no essential IAP | 3.1 | Cannot gate core functionality behind paywall without disclosure |
| Subscription terms clear | 3.1.2 | Duration, price, what happens on cancel |
| Free trial rules | 3.1.1 | Must state: duration, content losing access, charges |
| Loot box odds required | 3.1.1 | Disclose BEFORE purchase |
| No predatory lending | 5.1.3 | Max 36% APR, no 60-day repayment |

### Google Play
| Rule | Reference | Detail |
|------|-----------|--------|
| No pricing in metadata | Metadata Policy | No "$X.XX", "free", "on sale" |
| Financial features declaration | Financial Policy | Mandatory since Oct 2025 |
| No deceptive financial products | Financial Policy | |
| Subscription disclosure | Billing Policy | Clear terms before purchase |

## Health & Medical Claims

### Apple App Store
| Rule | Reference | Detail |
|------|-----------|--------|
| No unvalidated measurements | 5.1.2 | Cannot claim BP, temp, glucose, SpO2 via phone sensors alone |
| Must disclose methodology | 5.1.2 | If claiming health accuracy |
| No health data for ads/marketing | 5.1.2 | HealthKit data restricted |
| No false health data writing | 5.1.2 | Cannot write inaccurate data to HealthKit |
| Research apps need ethics review | 5.1.2 | IRB approval required |
| Remind users to consult doctor | 5.1.2 | Before medical decisions |

### Google Play
| Rule | Reference | Detail |
|------|-----------|--------|
| No misleading health claims | Health Policy | Without regulatory proof |
| No contradicting medical consensus | Health Policy | |
| No unapproved substances | Health Policy | |
| EU medical device labeling | Health Policy (2025) | MDCG guidance for EU apps |
| Health disclaimers required | Health Policy | For health-related functionality |

## Review Manipulation

### Both Platforms
| Rule | Reference | Detail |
|------|-----------|--------|
| No incentivized reviews | Apple 3.2.2 / Google Reviews Policy | No rewards for reviews |
| No fake testimonials | Both metadata policies | No "users love us" without evidence |
| No rating manipulation | Both | No bulk fake reviews |
| No review brigading | Both | No coordinated review campaigns |

### Google Play Specific
| Rule | Reference | Detail |
|------|-----------|--------|
| ML detection active | Reviews Policy | Same IPs, patterns, spikes detected |
| Violations = suspension | Reviews Policy | Or account termination |

## AI Content Policies

### Apple App Store (Nov 2025)
| Rule | Reference | Detail |
|------|-----------|--------|
| Disclose third-party AI data sharing | Privacy (2025) | Explicit user consent required |
| Failure to disclose = rejection | Privacy (2025) | Actively enforced |

### Google Play (Jul 2025)
| Rule | Reference | Detail |
|------|-----------|--------|
| In-app reporting for AI content | AI Policy | Users must be able to flag offensive content |
| Content filtering required | AI Policy | Prevent offensive generation |
| Deepfake restrictions | AI Policy | Voice/video deepfakes regulated |
| Developer responsible for output | AI Policy | |

## Intellectual Property

### Both Platforms
| Rule | Reference | Detail |
|------|-----------|--------|
| No competitor brand names | Apple 4.1(c) / Google IP Policy | In any metadata field |
| No trademarked terms without license | Both | Written permission required |
| No impersonation | Both | Cannot imply endorsement/relationship |
| "Unofficial" label doesn't help | Google IP Policy | Still can't use others' branding |

### Apple-Specific
| Rule | Reference | Detail |
|------|-----------|--------|
| No Apple product names as keywords | 2.3.7 | Unless describing genuine compatibility |
| No other marketplace references | 2.3.10 | No "also on Google Play" |

## Banned Words & Phrases

### Google Play Title (PROHIBITED)
`#1`, `best`, `top`, `free`, `no ads`, `ad free`, `ad-free`, `new`, `hot`, `sale`, `discount`, `limited time`, `download now`, `install now`, `play now`, `try now`, `update now`, `get it now`

### Google Play Short Description (PROHIBITED)
All title banned words PLUS: user testimonials, star ratings, performance claims, emoji, ALL CAPS phrases

### Google Play Screenshots (PROHIBITED TEXT)
`#1`, `Best app`, `Top`, `Million downloads`, `Most popular`, `Award winning`, `Sale`, `Discount`, `Free`, `Download now`, `Install now`, ranking claims, pricing information

### Apple (PROHIBITED in any metadata)
Competitor brand names, other platform names (Android, Google Play, Samsung), pricing terms, trademarked terms you don't own, irrelevant popular terms

## Enforcement Severity

| Severity | Meaning | Examples |
|----------|---------|---------|
| **VIOLATION** | Will likely cause rejection or removal | Competitor names, banned words in title, fake screenshots |
| **RISK** | May trigger review or penalty | Keyword stuffing, borderline claims, missing disclosures |
| **ADVISORY** | Best practice, not strictly enforced | Suboptimal IAP disclosure, missing health disclaimer |
