# softballR Repository Summary
*NCAA Softball Data Analysis Resource*

---

## Available Seasons by Data Source

| Data Source | Data Type | Seasons Available |
|-------------|-----------|-------------------|
| **NCAA D1** | Scoreboard | 2012-2024 |
| **NCAA D2/D3** | Scoreboard | 2016-2024 |
| **NCAA** | Player Box (Hitting/Pitching) | 2016-2024 |
| **NCAA** | Player Box (Fielding) | 2023 only |
| **NCAA** | Play-by-Play | 2021-2024 |
| **NCAA** | Rosters | 2021-2023 |
| **ESPN** | Scoreboard | 2015-2023 |
| **NAIA** | Scoreboard/PBP | 2023 only |

---

## Statistics Available by File Type

### Player Box Scores (Hitting)
`player, pos, g, rbi, ab, r, h, 2b, 3b, tb, hr, ibb, bb, hbp, sf, sh, k, dp, sb, cs, picked`

### Player Box Scores (Pitching)
`ip, ha (hits allowed), er, bb, hb, so, bf (batters faced), hr_a (home runs allowed)`

### Play-by-Play Data
- Game state: `inning, top_bottom, away_team_runs, home_team_runs`
- Event tracking for 23 play outcomes including: strikeouts (swinging/looking), groundouts, flyouts, double plays, errors, walks, HBP, singles, doubles, triples, home runs

### Team Box Scores (ESPN)
- 25 batting metrics
- 29 pitching metrics
- 17 fielding metrics

### Rankings Data
Four sources with different methodologies: RPI, D1Softball Top 25, USA Today/NFCA (with first-place votes), Massey Ratings (win%, delta, conference)

### Roster Data
Team rosters with player information (2021-2023)

---

## Suggested Use Cases for Your Sports Data Analysis

1. **Player Performance Trend Analysis**
   Track individual player statistics across multiple seasons to identify improvement trajectories, breakout candidates, or declining performance. The 2016-2024 hitting/pitching data provides 8+ years of longitudinal data for D1 athletes.

2. **Game Situation Analysis**
   Use the play-by-play data (2021-2024) to analyze clutch performance, late-inning success rates, or how teams perform in specific game states (runners in scoring position, two-out situations, etc.).

3. **Recruiting & Transfer Portal Intelligence**
   Combine roster data with player box scores to track where top performers transfer, identify programs that develop talent, or spot under-recruited conferences producing high performers.

---

## Portfolio Project Ideas

### Project 1: NCAA Softball Win Probability Model
Build a live win probability model using the play-by-play data. Calculate win expectancy at each game state based on inning, score differential, and base/out situations. Create visualizations showing win probability charts for notable games. *Tech stack: Python/R, statistical modeling, interactive viz with Plotly or Shiny*

### Project 2: Conference Performance Dashboard
Create an interactive dashboard comparing conference strength across multiple metrics: RPI rankings, non-conference winning percentage, postseason success rates, and player statistical averages. Include year-over-year trends from 2016-2024. *Tech stack: Tableau/Power BI or R Shiny, data aggregation, comparative analytics*

### Project 3: Pitcher Effectiveness Analyzer
Build a tool that evaluates pitcher performance beyond traditional stats. Use play-by-play data to calculate advanced metrics like strikeout rate by inning, performance with runners on base, ground ball vs fly ball tendencies (inferred from out types), and opponent quality adjustments using RPI data. *Tech stack: Python, feature engineering, statistical analysis, web app deployment*

---

*Data Source: [sportsdataverse/softballR](https://github.com/sportsdataverse/softballR) - maintained by SportsDataVerse*
