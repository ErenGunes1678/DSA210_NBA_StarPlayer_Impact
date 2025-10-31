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
The analysis will focus on:

- **Correlation Measurement**  
  - How strongly a star player's performance correlates with team wins or losses.  

- **Performance Comparison**  
  - Comparing team win rates when the star performs above vs. below their average stats.  

- **Visualization**  
- Using **statistical and visualization techniques** to illustrate how individual player impact varies between stars and across teams

---

## Expected Findings  
- Star players likely have a measurable influence on win probability.  
- However, the **degree of dependence** may vary – some teams rely heavily on one player, while others perform well through teamwork.  
- Stats like **assists, efficiency, and turnovers** may predict success better than just total points.  
- Balanced teams may maintain wins even when their star player underperforms.  

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
