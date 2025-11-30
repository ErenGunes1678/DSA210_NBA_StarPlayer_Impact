# DSA210_NBA_StarPlayer_Impact  
**Sabancı University – DSA210 Term Project**

---

## Abstract  
As an NBA fan, I often see discussions about how much a single superstar impacts a team's success. Does having a player like **LeBron James, Stephen Curry, or Nikola Jokić** actually increase a team's chances of winning, or does teamwork matter more?  

Since the **MVP (Most Valuable Player)** award is considered one of the most important individual honors in the NBA, this project aims to explore:  
**How much does a star player actually affect the outcome of an NBA game?**  

This project will use real NBA statistical data to **quantify the influence of star players on team performance and game results**.

---

## Data Sources  
The data for this project will be collected from the following publicly available sources:

- **Kaggle Dataset:** https://www.kaggle.com/datasets/nathanlauga/nba-games  
- **NBA Official Stats:** https://www.nba.com/stats  
- **ESPN Player Game Logs:** https://www.espn.com/nba/player/gamelog/_/id/3975/type/nba/year/2017

These sources provide:  
- Player-level stats: points, assists, rebounds, turnovers, shooting percentages  
- Team-level stats: win/loss result, opponent scores, home vs away games  
- Game metadata: date, team names, player names, minutes played, etc.

---

## Data Preparation

The dataset will be cleaned to:
- Remove duplicates  
- Handle missing or incorrect values  
- Merge player and team data into a usable structure
  
- **Filtering Players and Games**  
   - Focus on MVPs, All-Star players, or statistical leaders of each team.  

- **Merging Data Sources**  
   - Combine game results with individual player performance statistics.  

- **Creating New Metrics**  
   - Examples:  
     - Player Impact Score  
     - Percentage of team points scored (Points Share)  
      
---

## Data Analysis Plan

The analysis combines **completed work so far** and **planned future steps**:

- **Correlation Analysis (completed)**  
  - Measure how strongly star performance metrics (points, rebounds, assists, points share, etc.) correlate with team point differential and win/loss outcomes.

- **Performance Comparison (completed)**  
  - Compare team win rates when a star player scores **above** vs. **below** their typical (median) point total.  
  - Compare average star points in games their team **wins** versus games they **lose** using formal hypothesis tests.

- **Hypothesis Testing (completed)**  
  - Two-proportion z-test for the difference in win rate between high-scoring and low-scoring star games.  
  - Welch two-sample t-test for the difference in average star points between wins and losses.

- **Visualization (completed and ongoing)**  
  - Use histograms, boxplots and correlation heatmaps to visualize how individual star performance relates to game outcomes.  
  - Highlight differences between selected stars in terms of distribution of points and contribution to team scoring (points share).

- **Extended Modeling (planned)**  
  - Build predictive models (e.g., logistic regression) to estimate win probability as a function of star and team statistics.  
  - Compare model performance when using only star statistics versus using broader team statistics to understand how “star-dependent” different teams are.

---

## Preliminary Results (So Far)

Based on the current dataset and analysis of selected star players (LeBron James, Stephen Curry, Kevin Durant, James Harden, Nikola Jokić):

- Teams win about **69%** of games when their star scores **above** their own median point total, compared to about **62%** when the star scores **below** the median.  
  - A two-proportion z-test shows this difference (≈ **6.9 percentage points**) is **statistically significant** (p-value ≈ 4.96 × 10⁻⁷).

- Star players score on average about **26.3 points** in games their team **wins** and about **23.9 points** in games their team **loses**.  
  - A Welch t-test indicates this difference (≈ **2.4 points**) is also **statistically significant** (p-value ≈ 1.21 × 10⁻¹⁶).

These preliminary results provide quantitative evidence that higher individual scoring by star players is associated with both higher win probability and higher average scoring in wins.

---

## Expected Findings (Updated)

The project is still in progress, but based on the initial analysis and planned next steps, the expected findings are:

- **Star players do have a measurable influence on win probability.**  
  The current tests already show that when a star scores more than usual, their team’s chance of winning increases.

- The **degree of dependence** on a single star is likely to vary by team and context.  
  Some teams might be highly sensitive to star scoring, while more balanced teams may rely less on a single player.

- While total points are clearly important, additional metrics such as **shooting efficiency**, **assists** and **turnovers** may further improve the prediction of game outcomes.  
  These variables will be explored in later stages using correlation analysis and predictive models.

- **Balanced teams** may be able to maintain a relatively high win rate even when their star underperforms, whereas star-centric teams may experience larger drops in win probability when their main scorer has a low-impact game.

These expectations will be refined and tested as more players, metrics and modeling approaches are incorporated into the analysis.


---

## Limitations  
- The dataset only contains **numerical statistics** — it does not capture:  
  - Defensive gravity (double-teams, off-ball pressure)  
  - Leadership, clutch performance, or emotional impact  
  - Coaching strategy or injuries  

- Example: If a star player is double-teamed and creates scoring chances for others, this might not fully show up in basic statistics.

---

## Tools & Technologies  
- **Programming Language:** Python  
- **Libraries:** pandas, numpy, matplotlib, seaborn, scikit-learn  
- **Environment:** Jupyter Notebook  
- **Version Control:** Git & GitHub  

---
