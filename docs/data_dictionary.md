# NCAA Softball Data Dictionary
*softballR Dataset Reference*

---

## Overview

This document provides detailed field definitions for all datasets available from the [sportsdataverse/softballR](https://github.com/sportsdataverse/softballR) repository. Data is sourced from NCAA, ESPN, and NAIA.

---

## 1. Team Info Dataset

**Source**: `ncaa_team_info.RDS`
**Description**: Season-level team information including record, conference, and coaching staff
**Total Records**: ~41,000 (all divisions, all seasons)

| Field | Type | Description |
|-------|------|-------------|
| `team_name` | string | Official team name (e.g., "Oklahoma", "UCLA") |
| `team_id` | string | NCAA unique team identifier |
| `season` | string | Season year (e.g., "2024", "2025") |
| `head_coach` | string | Head coach name |
| `division` | string | NCAA division: "D-I", "D-II", "D-III" |
| `conference` | string | Conference name (e.g., "SEC", "Big 12", "Pac-12") |
| `wins` | integer | Total season wins |
| `losses` | integer | Total season losses |
| `ties` | integer | Total season ties |
| `win_perc` | float | Winning percentage (0.0 - 1.0) |

---

## 2. Scoreboard Dataset

**Source**: `ncaa_scoreboard_{year}.RDS`
**Description**: Game-level results with final scores
**Records per Season**: ~8,000 games (D1)

| Field | Type | Description |
|-------|------|-------------|
| `away_team` | string | Away team name |
| `away_team_id` | string | NCAA team ID for away team |
| `away_team_logo` | string | URL to team logo image |
| `away_team_runs` | float | Final runs scored by away team |
| `home_team` | string | Home team name |
| `home_team_id` | string | NCAA team ID for home team |
| `home_team_logo` | string | URL to team logo image |
| `home_team_runs` | float | Final runs scored by home team |
| `game_date` | string | Game date (format: "MM/DD/YYYY" or "MM/DD/YYYY HH:MM AM/PM") |
| `game_id` | string | Unique game identifier |
| `status` | string | Game status: "Final", "Canceled", "Postponed", etc. |

---

## 3. Hitting Box Scores Dataset

**Source**: `d1_hitting_box_scores_{year}.RDS`
**Description**: Player-level batting statistics per game
**Records per Season**: ~200,000+ player-game records (D1)

| Field | Type | Description |
|-------|------|-------------|
| `player` | string | Player name (format: "Last, First") |
| `pos` | string | Position played (SS, CF, P, DH, etc.) |
| `g` | float | Games (always 1 for box score) |
| `ab` | float | At bats |
| `r` | float | Runs scored |
| `h` | float | Hits |
| `x2b` | float | Doubles |
| `x3b` | float | Triples |
| `hr` | float | Home runs |
| `rbi` | float | Runs batted in |
| `tb` | float | Total bases |
| `bb` | float | Walks (bases on balls) |
| `ibb` | float | Intentional walks |
| `hbp` | float | Hit by pitch |
| `k` | float | Strikeouts (swinging) |
| `kl` | float | Strikeouts (looking) |
| `sf` | float | Sacrifice flies |
| `sh` | float | Sacrifice hits (bunts) |
| `dp` | float | Double plays |
| `gdp` | float | Grounded into double play |
| `tp` | float | Triple plays |
| `sb` | float | Stolen bases |
| `cs` | float | Caught stealing |
| `picked` | float | Picked off |
| `go` | float | Ground outs |
| `fo` | float | Fly outs |
| `team` | string | Player's team name |
| `opponent` | string | Opposing team name |
| `game_id` | string | Unique game identifier |
| `game_date` | string | Game date |
| `season` | float | Season year |

### Derived Metrics (Calculate Yourself)

| Metric | Formula |
|--------|---------|
| Batting Average (AVG) | `h / ab` |
| On-Base Percentage (OBP) | `(h + bb + hbp) / (ab + bb + hbp + sf)` |
| Slugging Percentage (SLG) | `tb / ab` |
| OPS | `OBP + SLG` |
| Total Strikeouts | `k + kl` |

---

## 4. Pitching Box Scores Dataset

**Source**: `d1_pitching_box_scores_{year}.RDS`
**Description**: Player-level pitching statistics per game
**Records per Season**: ~30,000 pitcher-game records (D1)

| Field | Type | Description |
|-------|------|-------------|
| `player` | string | Pitcher name (format: "Last, First") |
| `ip` | float | Innings pitched (e.g., 5.2 = 5 2/3 innings) |
| `ha` | float | Hits allowed |
| `er` | float | Earned runs |
| `bb` | float | Walks (bases on balls) |
| `hb` | float | Hit batters |
| `so` | float | Strikeouts |
| `bf` | float | Batters faced |
| `hr_a` | float | Home runs allowed |
| `go` | float | Ground outs induced |
| `fo` | float | Fly outs induced |
| `team` | string | Pitcher's team name |
| `opponent` | string | Opposing team name |
| `game_id` | string | Unique game identifier |
| `season` | float | Season year |

### Derived Metrics (Calculate Yourself)

| Metric | Formula |
|--------|---------|
| ERA | `(er / ip) * 7` (7 innings in softball) |
| WHIP | `(ha + bb) / ip` |
| K/9 | `(so / ip) * 7` |
| BB/9 | `(bb / ip) * 7` |
| K/BB | `so / bb` |
| GO/FO (Ground/Fly Ratio) | `go / fo` |

---

## 5. Play-by-Play Dataset

**Source**: `d1_ncaa_pbp_{year}.RDS`
**Description**: At-bat level play descriptions with game state
**Records per Season**: ~470,000 plays (D1)

| Field | Type | Description |
|-------|------|-------------|
| `game_id` | string | Unique game identifier |
| `team` | string | Team currently batting |
| `opponent` | string | Team currently fielding |
| `inning` | float | Inning number (1-7+) |
| `top_bottom` | string | "top" or "bottom" of inning |
| `away_team_runs` | string | Cumulative away team runs |
| `home_team_runs` | string | Cumulative home team runs |
| `events` | string | Full text description of play outcome |
| `play_id` | string | Unique play identifier (format: `{game_id}_{inning}_{half}_{sequence}`) |
| `game_date` | string | Game date |

### Event Types (Parsed from `events` field)

The `events` field contains raw text that can be parsed for:

| Event Category | Example Text Patterns |
|----------------|----------------------|
| Strikeout (swinging) | "struck out swinging" |
| Strikeout (looking) | "struck out looking" |
| Groundout | "grounded out to ss/2b/3b/1b/p" |
| Flyout | "flied out to lf/cf/rf" |
| Popout | "popped up to" |
| Lineout | "lined out to" |
| Single | "singled to/through" |
| Double | "doubled to" |
| Triple | "tripled to" |
| Home Run | "homered to" |
| Walk | "walked" |
| Hit By Pitch | "hit by pitch" |
| Error | "reached on an error" |
| Fielder's Choice | "fielder's choice" |
| Sacrifice | "sacrifice fly/bunt" |
| Stolen Base | "stole" |
| Double Play | "double play" |

---

## Key Identifiers

| ID Field | Description | Example |
|----------|-------------|---------|
| `game_id` | Unique game identifier | "4497537" |
| `team_id` | NCAA team code | "572030" |
| `play_id` | Unique play within game | "4497537_1_0_3" |

### Joining Datasets

```
scoreboard.game_id = hitting_box.game_id = pitching_box.game_id = play_by_play.game_id
team_info.team_name = scoreboard.home_team (or away_team)
```

---

## Data Quality Notes

1. **Missing Values**: Some fields may contain NaN/NULL, especially for partial games or canceled contests
2. **Name Variations**: Player names may have slight variations across seasons (married names, nicknames)
3. **Conference Realignment**: Conference affiliations change year-to-year; use `team_info` for accurate season-specific data
4. **Innings Pitched Format**: `ip` uses decimal notation where .1 = 1/3 inning, .2 = 2/3 innings

---

*Data Source: [sportsdataverse/softballR-data](https://github.com/sportsdataverse/softballR-data)*
