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

- **Correlation Analysis**  
  - Measure how strongly star performance metrics (points, rebounds, assists, points share, etc.) correlate with team point differential and win/loss outcomes.

- **Performance Comparison**  
  - Compare team win rates when a star player scores **above** vs. **below** their typical (median) point total.  
  - Compare average star points in games their team **wins** versus games they **lose** using formal hypothesis tests.

- **Hypothesis Testing**  
  - Two-proportion z-test for the difference in win rate between high-scoring and low-scoring star games.  
  - Welch two-sample t-test for the difference in average star points between wins and losses.

- **Visualization**  
  - Use histograms, boxplots and correlation heatmaps to visualize how individual star performance relates to game outcomes.  
  - Highlight differences between selected stars in terms of distribution of points and contribution to team scoring (points share).

- **Extended Modeling**  
  - Built supervised ML classification models to predict `star_team_win` (win/loss from the star’s team perspective).  
  - Implemented and compared a Dummy (majority-class) baseline, Logistic Regression, Decision Tree, and k-Nearest Neighbors (kNN).  
  - Compared three feature sets:  
    - **S (Star-only):** star box-score statistics  
    - **SC (Star + Context):** S + home/away + season  
    - **ST (Star + Team totals):** SC + team totals and points share  
  - Used a temporal train/validation/test split by season (train ≤ 2019, validation 2020–2021, test ≥ 2022) and selected models based on validation performance, then reported final test results.


---

## Preliminary Results(Consist of Hypotesis Testing)

Based on the current dataset and analysis of selected star players (LeBron James, Stephen Curry, Kevin Durant, James Harden, Nikola Jokić):

- Teams win about **69%** of games when their star scores **above** their own median point total, compared to about **62%** when the star scores **below** the median.  
  - A two-proportion z-test shows this difference (≈ **6.9 percentage points**) is **statistically significant** (p-value ≈ 4.96 × 10⁻⁷).

- Star players score on average about **26.3 points** in games their team **wins** and about **23.9 points** in games their team **loses**.  
  - A Welch t-test indicates this difference (≈ **2.4 points**) is also **statistically significant** (p-value ≈ 1.21 × 10⁻¹⁶).

These preliminary results provide quantitative evidence that higher individual scoring by star players is associated with both higher win probability and higher average scoring in wins.

---


## Machine Learning Results

To complement hypothesis testing, I framed the problem as a binary classification task: predicting `star_team_win` (win/loss from the star team perspective).

- **Models compared:** Dummy baseline, Logistic Regression, Decision Tree, kNN  
- **Evaluation setup:** Train/Validation/Test split by season (train ≤ 2019, validation 2020–2021, test ≥ 2022)  
- **Feature sets compared:**  
  - S (star-only), SC (star + context), ST (star + team totals and points share)

**Key result:** The trained ML models outperform the Dummy baseline and achieve high ROC-AUC on validation/test, especially when using ST features. This supports the conclusion that star performance has meaningful predictive signal, and adding team-level context improves predictive power further.

<img width="920" height="123" alt="image" src="https://github.com/user-attachments/assets/0609faea-8f9f-49ef-b936-9708fd084b1c" />

- For Final LogReg(ST), the model correctly predicts 69 wins and 45 losses, with 15 false-win and 8 false-loss errors on the test set.
---

## Findings

Based on both the initial statistical analysis (EDA + hypothesis testing) and the machine learning models, the expected findings of this project are:

### 1) Star players have a measurable impact on winning
The early hypothesis tests suggest that when a star player performs better than their usual level, their team’s probability of winning increases. For example, games where the star scores above their own median tend to have a higher win rate than games where the star scores below it. This supports the idea that star performance is not just “random noise,” but is meaningfully connected to game outcomes.

### 2) Stars tend to score more in wins than in losses
The second hypothesis test indicates that star players score more points on average in games their team wins compared to games their team loses. This reinforces the idea that star performance (especially scoring) is associated with team success, even though it is not the only factor.

### 3) Machine learning models should predict wins better than a naive baseline
In the ML stage, a DummyClassifier baseline (predicting the majority outcome) provides a minimum performance reference point. The expectation is that real supervised learning models (Logistic Regression, Decision Tree, kNN) will outperform this baseline using star statistics, showing that the relationship between star performance and winning can be captured predictively, not only through hypothesis tests.

### 4) Star only features will already contain meaningful predictive signal
Even when using only star box score features (S) or star features plus simple context like home/away and season (SC), the models are expected to achieve strong performance (higher ROC-AUC and balanced accuracy than the dummy baseline). This would imply that a single star’s output (points, assists, rebounds, minutes, efficiency, turnovers) contains enough information to meaningfully estimate win probability.

### 5) Adding team level totals will further improve prediction, showing teamwork still matters
When the models include team level totals and share based variables (ST), predictive performance is expected to improve further. This does not contradict star impact; instead, it suggests that while star performance is important, the overall team context (total scoring, team rebounds/assists, etc.) strengthens the explanation of game results. In other words, star performance matters, but it works within a broader team system.

### 6) Dependence on a single star likely varies by team and game context
A key expected finding is that some teams are more star dependent than others. For example, teams where the star contributes a larger fraction of team scoring (higher points share) may show a bigger drop in win probability when the star underperforms. More balanced teams may maintain stronger win chances even when the star has a lower-impact game.

### 7) Efficiency and mistakes (turnovers) should be important alongside raw points
Beyond total points, the expected outcome is that shooting efficiency (FG%, 3P%, FT%) and negative contributions like turnovers will meaningfully affect win prediction. This aligns with real basketball intuition: a star scoring 30 points on very poor efficiency or with many turnovers may not increase win probability as much as a more efficient performance.

### Overall takeaway
Combining both approaches, the project is expected to conclude that star players do have a statistically measurable and predictively meaningful impact on game outcomes. However, machine learning comparisons should also show that including team level context improves predictions, supporting the more balanced conclusion: star performance is an important factor, but it is not the only determinant of winning.


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

- **Core Data Libraries:**  
  - pandas, numpy (data loading, cleaning, feature engineering)

- **Statistical Analysis:**  
  - scipy (hypothesis testing: z-test, Welch t-test)

- **Visualization:**  
  - matplotlib, seaborn (histograms, boxplots, correlation heatmaps, evaluation plots)

- **Machine Learning (ML):**  
  - scikit-learn  
  - preprocessing: SimpleImputer, StandardScaler  
  - pipelines: Pipeline, ColumnTransformer  
  - models: DummyClassifier, LogisticRegression, DecisionTreeClassifier, KNeighborsClassifier  
  - evaluation: accuracy, precision, recall, F1-score, confusion matrix, ROC-AUC

- **Data Source Access:**  
  - kagglehub (downloading the NBA dataset programmatically)

- **Environment:** Jupyter Notebook (Google Colab compatible)  

- **Version Control:** Git & GitHub  


---
