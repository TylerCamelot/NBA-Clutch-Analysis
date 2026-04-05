# 🏀 NBA Clutch Performance Analysis

## Overview  
This project analyzes **NBA player performance in clutch situations** to determine what makes a player reliable under pressure.

The goal is to:
- Develop a **quantitative metric for clutch performance (CPI)**
- Identify **which players coaches can trust late in games**
- Use **machine learning to predict clutch ability** based on earlier game performance and career indicators

---

## Objectives  

- Create a **Clutch Performance Index (CPI)** to measure player effectiveness in high-pressure moments  
- Identify **key drivers of clutch performance** using predictive modeling  
- Provide **actionable insights for coaching decisions**

---

## Key Concept: Clutch Performance Index (CPI)

- CPI is a **normalized score (0–1)** representing a player’s likelihood of performing well in clutch time  
- Derived from:
  - Scoring efficiency  
  - Defensive contributions (steals, blocks)  
  - Turnovers  
- Designed to reflect **true performance under pressure**, not just volume stats  

---

## Dataset  

The dataset combines multiple sources:
- Play-by-play NBA data (clutch situations)
- All-Star selections (experience proxy)
- Award history (performance recognition)

**Clutch Definition:**
- Final 5 minutes of Q4 or overtime  
- Score margin ≤ 5 points  

---

## Methodology  

### 1. Data Preparation  
- Filtered for **clutch-eligible players**  
- Merged datasets using player identifiers  
- Created engineered features:
  - Early game stats (Q1–Q3)
  - Career indicators (All-Star, awards)

---

### 2. Feature Selection  

**Model Inputs (No Data Leakage):**
- Early game performance:
  - `q13_made_fg`, `q13_fg_pct`
  - `q13_blocks`, `q13_steals`, `q13_turnovers`
- Experience indicators:
  - `allstar_count`, `award_wins`, `mvp_shares`

---

### 3. Modeling Framework  

1. Define features and target (CPI)  
2. Train-test split  
3. Train models:
   - Ridge Regression  
   - Random Forest  
   - Gradient Boosting  
4. Perform 5-fold cross-validation  
5. Select best model based on CV R²  
6. Fit final model  
7. Evaluate on test set (R², RMSE, MAE)  
8. Interpret results  
9. Residual analysis  

---

## Results  

- CPI distribution across ~2,700 players shows:
  - Mean CPI ≈ 0.11  
  - Strong right skew (few elite clutch players)  

### Key Insights:
- **Early-game efficiency is highly predictive of clutch performance**
- **Turnovers significantly reduce clutch reliability**
- **Defensive contributions (steals/blocks) matter more than expected**
- Experience (All-Star / awards) provides **moderate predictive value**

---

## Visualizations  

- CPI distribution  
- Top clutch players ranking  
- Feature importance analysis  
- Scatter plots (e.g., FG% vs CPI)

---

## Key Takeaways  

- Coaches should prioritize players with:
  - Strong early-game efficiency  
  - Low turnover rates  
  - Defensive impact  

- Clutch performance is **predictable**, not purely random  

---

## Limitations  

- Does not account for defensive pressure or game difficulty 
- No adjustment for team context or play design
- Sample size varies, even with the minutes adjustment some players have limited clutch opportunities compared to others  

---

## Future Improvements  

- Bayesian adjustment for small sample sizes  
- Player archetype classification:
  - Clutch Elevator  
  - Steady  
  - Pressure Decliner  

---

## Tech Stack  

- Python (pandas, numpy, scikit-learn)  
- Matplotlib / Seaborn  
- Jupyter Notebook  

---
