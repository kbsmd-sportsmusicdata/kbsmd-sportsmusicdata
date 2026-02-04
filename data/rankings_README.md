# NCAA Softball Rankings Data

## Data Sources

Rankings data compiled from multiple sources via web search results:

- **RPI**: NCAA Rating Percentage Index (official NCAA metric)
- **D1Softball**: D1Softball.com Top 25 Poll
- **USA Softball/ESPN**: ESPN.com/USA Softball Collegiate Top 25 Poll
- **NFCA**: National Fastpitch Coaches Association Poll
- **Softball America**: Softball America Top 25

## 2025 Season (Final Rankings)

| File | Description |
|------|-------------|
| `2025/ncaa_rpi_rankings_2025.csv` | Final 2025 RPI rankings (Top 25) |
| `2025/d1softball_top25_2025_final.csv` | Final D1Softball Top 25 Poll |

### Key 2025 Results
- **National Champion**: Texas (snapped Oklahoma's 4-year title run)
- **National Runner-up**: Texas Tech
- **No. 1 Overall Seed**: Texas A&M
- **WCWS Semifinalists**: Oklahoma, Tennessee

## 2026 Season (Preseason Rankings)

| File | Description |
|------|-------------|
| `2026/preseason_rankings_2026.csv` | Multi-source preseason rankings with poll attribution |
| `2026/d1softball_preseason_top25_2026.csv` | Consolidated D1Softball-style preseason Top 25 |

### 2026 Preseason Highlights
- Texas Tech and Texas tied for No. 1 in ESPN/USA Softball poll
- Oklahoma consensus No. 3 across all polls
- Season begins February 5, 2026

## Data Limitations

**Important**: These rankings were compiled from web search results due to access restrictions on primary sources. The data represents:

1. **Top 10-15 teams**: High confidence - confirmed across multiple sources
2. **Teams 16-25**: Moderate confidence - extrapolated from partial data
3. **Full RPI lists**: Not available - primary sources (NCAA.com, WarrenNolan.com) blocked access

For official complete rankings, visit:
- [NCAA.com RPI](https://www.ncaa.com/rankings/softball/d1/ncaa-womens-softball-rpi)
- [WarrenNolan.com](https://www.warrennolan.com/softball/2025/rpi-live)
- [D1Softball.com](https://d1softball.com/rankings/)

## Using softballR for Live Rankings

The softballR package includes functions to scrape live rankings:

```r
library(softballR)

# RPI Rankings
rpi <- ncaa_softball_rankings(source = "RPI")

# D1Softball Top 25
d1sb <- ncaa_softball_rankings(source = "D1Softball")

# USA Today/NFCA Poll
nfca <- ncaa_softball_rankings(source = "USA Today")

# Massey Ratings
massey <- ncaa_softball_rankings(source = "Massey")
```

Note: These functions require direct web access to source sites.
