# NCAA Softball Data

Data sourced from [sportsdataverse/softballR](https://github.com/sportsdataverse/softballR).

## Folder Structure

```
data/
├── ncaa_team_info.csv          # All teams, all seasons (2012-2025)
├── rankings_README.md          # Rankings data sources and limitations
├── 2024/
│   ├── ncaa_scoreboard_2024.csv
│   ├── d1_hitting_box_scores_2024.csv
│   └── d1_pitching_box_scores_2024.csv
├── 2025/
│   ├── ncaa_scoreboard_2025.csv
│   ├── d1_hitting_box_scores_2025.csv
│   ├── d1_pitching_box_scores_2025.csv
│   ├── ncaa_rpi_rankings_2025.csv        # Final 2025 RPI Top 25
│   └── d1softball_top25_2025_final.csv   # Final D1Softball Poll
└── 2026/
    ├── DATA_AVAILABILITY.md              # ⚠ Box scores not yet available — see note
    ├── preseason_rankings_2026.csv       # Multi-source preseason rankings
    └── d1softball_preseason_top25_2026.csv # D1Softball Preseason Top 25
```

> **2026 Box Scores**: The softballR data pipeline last ran August 2025 and has not
> yet reactivated for the 2026 season (started Feb 5, 2026). Box score CSVs will be
> added here once the source RDS files appear at `sportsdataverse/softballR-data`.
> See `2026/DATA_AVAILABILITY.md` for full details and options.

## Dataset Sizes

| File | Rows | Size |
|------|------|------|
| ncaa_team_info.csv | 41,138 | 2.2 MB |
| 2024 scoreboard | 7,989 | 1.4 MB |
| 2024 hitting | 218,578 | 35 MB |
| 2024 pitching | 30,886 | 2.8 MB |
| 2025 scoreboard | 8,098 | 1.5 MB |
| 2025 hitting | 187,745 | 25 MB |
| 2025 pitching | 31,603 | 2.9 MB |
| 2026 hitting | — | Not yet available |
| 2026 pitching | — | Not yet available |

## Documentation

See `/docs` for:
- `data_dictionary.md` - Field definitions and descriptions
- `data_schema.md` - Technical schema and relationships

## Data Source

Original RDS files from: https://github.com/sportsdataverse/softballR-data
