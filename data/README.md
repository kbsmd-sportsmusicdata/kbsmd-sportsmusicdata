# NCAA Softball Data

Data sourced from [sportsdataverse/softballR](https://github.com/sportsdataverse/softballR).

## Folder Structure

```
data/
├── ncaa_team_info.csv          # All teams, all seasons (2012-2025)
├── 2024/
│   ├── ncaa_scoreboard_2024.csv
│   ├── d1_hitting_box_scores_2024.csv
│   └── d1_pitching_box_scores_2024.csv
└── 2025/
    ├── ncaa_scoreboard_2025.csv
    ├── d1_hitting_box_scores_2025.csv
    └── d1_pitching_box_scores_2025.csv
```

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

## Documentation

See `/docs` for:
- `data_dictionary.md` - Field definitions and descriptions
- `data_schema.md` - Technical schema and relationships

## Data Source

Original RDS files from: https://github.com/sportsdataverse/softballR-data
