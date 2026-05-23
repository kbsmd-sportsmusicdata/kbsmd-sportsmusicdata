# NCAA Softball Data Schema
*Technical Schema Reference for softballR Datasets*

---

## File Formats

All source data from softballR is stored in **RDS format** (R Data Serialization). For Python users, use the `pyreadr` package to read these files.

### Reading Data

**R:**
```r
library(softballR)
team_info <- load_ncaa_softball_team_info()
scoreboard <- load_ncaa_softball_scoreboard(season = 2025, division = "D1")
hitting <- load_ncaa_softball_playerbox(season = 2025, category = "Hitting")
pitching <- load_ncaa_softball_playerbox(season = 2025, category = "Pitching")
pbp <- load_ncaa_softball_pbp(season = 2025, division = "D1")
```

**Python:**
```python
import pyreadr
import urllib.request
import tempfile

url = "https://github.com/sportsdataverse/softballR-data/raw/main/data/ncaa_scoreboard_2025.RDS"
with tempfile.NamedTemporaryFile(suffix='.rds', delete=False) as tmp:
    urllib.request.urlretrieve(url, tmp.name)
    result = pyreadr.read_r(tmp.name)
    df = list(result.values())[0]
```

---

## Schema Definitions

### 1. Team Info Schema

```json
{
  "table_name": "ncaa_team_info",
  "source_file": "ncaa_team_info.RDS",
  "primary_key": ["team_id", "season"],
  "record_count": 41138,
  "columns": {
    "team_name": {"type": "string", "nullable": false},
    "team_id": {"type": "string", "nullable": false},
    "season": {"type": "string", "nullable": false},
    "head_coach": {"type": "string", "nullable": true},
    "division": {"type": "string", "nullable": false, "values": ["D-I", "D-II", "D-III"]},
    "conference": {"type": "string", "nullable": true},
    "wins": {"type": "integer", "nullable": true},
    "losses": {"type": "integer", "nullable": true},
    "ties": {"type": "integer", "nullable": true},
    "win_perc": {"type": "float64", "nullable": true, "range": [0.0, 1.0]}
  }
}
```

### 2. Scoreboard Schema

```json
{
  "table_name": "ncaa_scoreboard",
  "source_file": "ncaa_scoreboard_{year}.RDS",
  "primary_key": ["game_id"],
  "record_count_per_year": 8000,
  "columns": {
    "away_team": {"type": "string", "nullable": false},
    "away_team_id": {"type": "string", "nullable": false},
    "away_team_logo": {"type": "string", "nullable": true},
    "away_team_runs": {"type": "float64", "nullable": true},
    "home_team": {"type": "string", "nullable": false},
    "home_team_id": {"type": "string", "nullable": false},
    "home_team_logo": {"type": "string", "nullable": true},
    "home_team_runs": {"type": "float64", "nullable": true},
    "game_date": {"type": "string", "nullable": false},
    "game_id": {"type": "string", "nullable": false},
    "status": {"type": "string", "nullable": false, "values": ["Final", "Canceled", "Postponed", "In Progress"]}
  }
}
```

### 3. Hitting Box Scores Schema

```json
{
  "table_name": "hitting_box_scores",
  "source_file": "d1_hitting_box_scores_{year}.RDS",
  "primary_key": ["game_id", "player", "team"],
  "record_count_per_year": 218000,
  "columns": {
    "player": {"type": "string", "nullable": false},
    "pos": {"type": "string", "nullable": true},
    "g": {"type": "float64", "nullable": true, "default": 1},
    "ab": {"type": "float64", "nullable": true},
    "r": {"type": "float64", "nullable": true},
    "h": {"type": "float64", "nullable": true},
    "x2b": {"type": "float64", "nullable": true},
    "x3b": {"type": "float64", "nullable": true},
    "hr": {"type": "float64", "nullable": true},
    "rbi": {"type": "float64", "nullable": true},
    "tb": {"type": "float64", "nullable": true},
    "bb": {"type": "float64", "nullable": true},
    "ibb": {"type": "float64", "nullable": true},
    "hbp": {"type": "float64", "nullable": true},
    "k": {"type": "float64", "nullable": true},
    "kl": {"type": "float64", "nullable": true},
    "sf": {"type": "float64", "nullable": true},
    "sh": {"type": "float64", "nullable": true},
    "dp": {"type": "float64", "nullable": true},
    "gdp": {"type": "float64", "nullable": true},
    "tp": {"type": "float64", "nullable": true},
    "sb": {"type": "float64", "nullable": true},
    "cs": {"type": "float64", "nullable": true},
    "picked": {"type": "float64", "nullable": true},
    "go": {"type": "float64", "nullable": true},
    "fo": {"type": "float64", "nullable": true},
    "team": {"type": "string", "nullable": false},
    "opponent": {"type": "string", "nullable": false},
    "game_id": {"type": "string", "nullable": false},
    "game_date": {"type": "string", "nullable": false},
    "season": {"type": "float64", "nullable": false}
  }
}
```

### 4. Pitching Box Scores Schema

```json
{
  "table_name": "pitching_box_scores",
  "source_file": "d1_pitching_box_scores_{year}.RDS",
  "primary_key": ["game_id", "player", "team"],
  "record_count_per_year": 31000,
  "columns": {
    "player": {"type": "string", "nullable": false},
    "ip": {"type": "float64", "nullable": true, "note": "Decimal format: 5.1 = 5 1/3 innings"},
    "ha": {"type": "float64", "nullable": true},
    "er": {"type": "float64", "nullable": true},
    "bb": {"type": "float64", "nullable": true},
    "hb": {"type": "float64", "nullable": true},
    "so": {"type": "float64", "nullable": true},
    "bf": {"type": "float64", "nullable": true},
    "hr_a": {"type": "float64", "nullable": true},
    "go": {"type": "float64", "nullable": true},
    "fo": {"type": "float64", "nullable": true},
    "team": {"type": "string", "nullable": false},
    "opponent": {"type": "string", "nullable": false},
    "game_id": {"type": "string", "nullable": false},
    "season": {"type": "float64", "nullable": false}
  }
}
```

### 5. Play-by-Play Schema

```json
{
  "table_name": "play_by_play",
  "source_file": "d1_ncaa_pbp_{year}.RDS",
  "primary_key": ["play_id"],
  "record_count_per_year": 470000,
  "columns": {
    "game_id": {"type": "string", "nullable": false},
    "team": {"type": "string", "nullable": false, "note": "Team at bat"},
    "opponent": {"type": "string", "nullable": false, "note": "Team in field"},
    "inning": {"type": "float64", "nullable": false, "range": [1, 15]},
    "top_bottom": {"type": "string", "nullable": false, "values": ["top", "bottom"]},
    "away_team_runs": {"type": "string", "nullable": true},
    "home_team_runs": {"type": "string", "nullable": true},
    "events": {"type": "string", "nullable": true, "note": "Raw play description text"},
    "play_id": {"type": "string", "nullable": false, "format": "{game_id}_{inning}_{half}_{sequence}"},
    "game_date": {"type": "string", "nullable": false}
  }
}
```

---

## Entity Relationship Diagram

```
┌─────────────────┐       ┌─────────────────┐
│   team_info     │       │   scoreboard    │
├─────────────────┤       ├─────────────────┤
│ team_id (PK)    │◄──────│ home_team_id    │
│ season (PK)     │       │ away_team_id    │
│ team_name       │       │ game_id (PK)    │
│ conference      │       │ game_date       │
│ division        │       │ status          │
│ wins/losses     │       └────────┬────────┘
└─────────────────┘                │
                                   │ game_id
         ┌─────────────────────────┼─────────────────────────┐
         │                         │                         │
         ▼                         ▼                         ▼
┌─────────────────┐       ┌─────────────────┐       ┌─────────────────┐
│  hitting_box    │       │  pitching_box   │       │  play_by_play   │
├─────────────────┤       ├─────────────────┤       ├─────────────────┤
│ game_id (FK)    │       │ game_id (FK)    │       │ game_id (FK)    │
│ player          │       │ player          │       │ play_id (PK)    │
│ team            │       │ team            │       │ inning          │
│ opponent        │       │ opponent        │       │ top_bottom      │
│ ab, h, hr, etc. │       │ ip, so, er, etc.│       │ events          │
└─────────────────┘       └─────────────────┘       └─────────────────┘
```

---

## Data Source URLs

| Dataset | URL Pattern |
|---------|-------------|
| Team Info | `https://github.com/sportsdataverse/softballR-data/raw/main/data/ncaa_team_info.RDS` |
| Scoreboard | `https://github.com/sportsdataverse/softballR-data/raw/main/data/ncaa_scoreboard_{year}.RDS` |
| Hitting Box (D1) | `https://github.com/sportsdataverse/softballR-data/raw/main/data/d1_hitting_box_scores_{year}.RDS` |
| Pitching Box (D1) | `https://github.com/sportsdataverse/softballR-data/raw/main/data/d1_pitching_box_scores_{year}.RDS` |
| Play-by-Play (D1) | `https://github.com/sportsdataverse/softballR-data/raw/main/data/d1_ncaa_pbp_{year}.RDS` |

---

## Available Years by Dataset

| Dataset | D1 | D2 | D3 |
|---------|----|----|----|
| Scoreboard | 2012-2025 | 2016-2025 | 2016-2025 |
| Hitting Box | 2012-2025 | 2016-2025 | 2016-2025 |
| Pitching Box | 2015-2025 | 2016-2025 | 2016-2025 |
| Play-by-Play | 2021-2025 | 2021-2025 | 2021-2025 |
| Team Info | All years combined in single file |

---

*Schema Version: 1.0 | Last Updated: February 2026*
