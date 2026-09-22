# 🏈 NFL Predictive Matchup & Betting Line Engine

An interactive sports analytics and predictive modeling application built with Python and Streamlit. The model ingests live `nflverse` play-by-play parquet data to project point spreads, over/under game totals, and expected team scores.

---

## 📊 Analytical Methodology

Raw EPA (Expected Points Added) models often produce unrealistic margins due to blowout garbage time and fluke turnover runbacks. This engine implements quant-style filtering and calibration techniques:

- **Garbage-Time Filtering:** Scrimmage snaps are filtered to competitive game states (Win Probability between 10% and 90%) to eliminate soft prevent-defense distortions.
- **Outlier Clamping:** Single-play EPA is bounded between `-3.0` and `+3.0` to prevent fluke defensive scores and extreme turnovers from skewing baseline team ratings.
- **Defensive Impact Regression:** Opposing defensive EPA allowed is regressed by 50% (`0.5` weight) to prevent double-counting efficiency and account for year-over-year defensive volatility.
- **Explosive Chunk Rate Calibration:** Over/under projections incorporate both drive pace and explosive play frequency (rushes ≥ 10 yds, passes ≥ 20 yds) against league baseline scoring standards.
- **Adjustable Stadium Dynamics:** Includes dynamic sliders for venue-specific Home Field Advantage (HFA) and situational defensive resistance weighting.

---

## 🚀 Key Features

- **Automated Data Ingestion:** Reads and caches complete regular-season `nflverse` play-by-play data via Parquet.
- **Interactive Matchup Predictor:** Instant head-to-head evaluation between any two NFL franchises.
- **Team Efficiency Dashboard:** Comparative breakdown showing EPA/play, Success Rate (EPA > 0), Explosive Play Rate, and competitive snaps per game.
- **Full League Leaderboards:** Sortable tables displaying all 32 offenses and defenses ranked by efficiency and point impact.

---

## 🛠 Tech Stack

- **Python 3.10+**
- **Streamlit** (UI and Web Deployment)
- **Pandas & NumPy** (Data processing and statistical aggregation)
- **PyArrow & Fastparquet** (High-performance Parquet ingestion)
- **nflverse** (Play-by-play data source)

---

## ⚙️ Local Setup

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/YOUR_USERNAME/nfl-matchup-model.git](https://github.com/YOUR_USERNAME/nfl-matchup-model.git)
   cd nfl-matchup-model
