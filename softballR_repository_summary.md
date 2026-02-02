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

### Project 1: 2024 Season Recap + 2025 Preview Dashboard
A timely, fan-focused project combining historical win probability analysis with forward-looking season preview content.

**Part A: "Best of 2024" Season Recap**
- **Most Dramatic Games**: Identify games with the largest win probability swings—comebacks, walk-offs, extra-inning thrillers
- **Clutch Performers**: Players with best stats in high-leverage situations (late innings, close games, RISP)
- **Conference Highlights**: Which conferences had the most competitive games? Biggest upsets by win probability differential?

**Part B: 2025 Season Preview**
- **Returning Stars**: Cross-reference 2024 player box scores with roster data to identify top performers coming back
- **Teams to Watch**: Programs that overperformed their preseason ranking vs final RPI
- **Opening Weekend Matchups**: Highlight marquee early-season games

**Why This Works**: Timely content fans want right now, demonstrates end-to-end data skills (historical analysis → predictive framing), and has natural social media shareability ("The 10 wildest games of 2024").

**Technical Approach**:
1. Pull 2024 play-by-play via `load_ncaa_softball_pbp(2024)`
2. Calculate win probability at each game state using historical base rates
3. Flag games where win prob crossed 50% multiple times or had >40% swings
4. Build Shiny app or static site with interactive game visualizations

*Tech stack: R/Python, statistical modeling, Shiny or Plotly Dash, potential social media integration*

### Project 2: Conference Performance Dashboard
Create an interactive dashboard comparing conference strength across multiple metrics: RPI rankings, non-conference winning percentage, postseason success rates, and player statistical averages. Include year-over-year trends from 2016-2024. *Tech stack: Tableau/Power BI or R Shiny, data aggregation, comparative analytics*

### Project 3: Pitcher Effectiveness Analyzer
Build a tool that evaluates pitcher performance beyond traditional stats. Use play-by-play data to calculate advanced metrics like strikeout rate by inning, performance with runners on base, ground ball vs fly ball tendencies (inferred from out types), and opponent quality adjustments using RPI data. *Tech stack: Python, feature engineering, statistical analysis, web app deployment*

---

*Data Source: [sportsdataverse/softballR](https://github.com/sportsdataverse/softballR) - maintained by SportsDataVerse*
