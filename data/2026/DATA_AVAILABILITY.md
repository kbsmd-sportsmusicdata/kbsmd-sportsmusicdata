# 2026 Season Box Score Data — Availability Notice

**Status as of February 2026: NOT YET AVAILABLE**

---

## What Was Checked

All known softballR data sources were checked for 2026 box score data:

| Source | Status | Last Updated |
|--------|--------|--------------|
| `sportsdataverse/softballR-data` | No 2026 files | August 7, 2025 |
| `tmking2002/softballR-data` | No 2026 files | August 7, 2025 |
| `stats.ncaa.org` (live scrape) | 403 Forbidden | — |
| Pre-compiled RDS (all accounts) | 404 Not Found | — |

## Why the Data Isn't Available

The softballR data pipeline runs via GitHub Actions and is maintained by the SportsDataVerse community. The pipeline:
- Ran actively during the 2025 season (Feb–Aug 2025)
- Went dormant after the 2025 season concluded
- Has **not yet been reactivated** for the 2026 season, which began February 5, 2026

This is a ~2-week gap at the start of the season — expected behavior for a community-maintained project.

## What IS in This Folder (2026)

| File | Contents |
|------|----------|
| `preseason_rankings_2026.csv` | Multi-source preseason Top 25 rankings |
| `d1softball_preseason_top25_2026.csv` | Consolidated D1Softball preseason poll |

## How to Get 2026 Data When Available

**Option 1 — Wait for pipeline to update (recommended)**
Check back at: https://github.com/sportsdataverse/softballR-data/tree/main/data
The `d1_hitting_box_scores_2026.RDS` and `d1_pitching_box_scores_2026.RDS` files
will appear once the maintainers reactivate the pipeline for the new season.

**Option 2 — Use softballR in R directly**
```r
install.packages("devtools")
devtools::install_github("sportsdataverse/softballR")
library(softballR)

# Once 2026 season IDs are available in the package:
hitting_2026  <- load_ncaa_softball_playerbox(season = 2026, category = "Hitting")
pitching_2026 <- load_ncaa_softball_playerbox(season = 2026, category = "Pitching")
```

**Option 3 — Monitor the repo and re-run download script**
When the RDS files appear at the source, re-run the Python download pattern used
for 2024/2025 data to pull and convert to CSV automatically.

---

*Checked: February 2026 | Re-check when pipeline shows new commits at sportsdataverse/softballR-data*
