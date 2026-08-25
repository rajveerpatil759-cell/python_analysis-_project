#  Netflix Content Strategy Analysis

> Exploratory Data Analysis of 8,800+ Netflix titles to uncover content strategy shifts, geographic expansion patterns, and seasonal acquisition behaviour using Python.

---

##  Project Overview

**Project Title:** Netflix Content Strategy Analysis
**Tool:** Python (pandas, matplotlib, seaborn)

This project analyses Netflix's content library (2008–2021) to answer 7 specific business questions about content strategy, geographic expansion, genre trends, and acquisition patterns — translating raw streaming data into actionable content strategy insights.

**Tools Used:**
-  Python — analysis and visualization
-  pandas — data cleaning and feature engineering
-  matplotlib & seaborn — data visualization
-  GitHub — version control

---

##  Repository Structure

```
netflix-analysis/
│
├── netflix_titles.csv
├── netflix_analysis.ipynb
└── README.md
```

---

## 📊 Dataset Overview

| Metric | Value |
|--------|-------|
| Total Titles | 8,807 |
| Content Types | Movies, TV Shows |
| Period Covered | 2008 — 2021 |
| Countries | 100+ |
| Columns | 12 |

**Columns:** show_id, type, title, director, cast, country, date_added, release_year, rating, duration, listed_in, description

---

##  Data Cleaning & Feature Engineering

### Cleaning Steps
- Filled missing values — director, cast, country, rating, duration
- Converted `date_added` to datetime with mixed format handling
- Dropped rows with null `date_added` (less than 1% of data)
- Extracted `year_added` and `month_added` from date column

### Engineered Feature
```python
# How old was content when Netflix acquired it?
df['content_age_when_added'] = df['year_added'] - df['release_year']
```
This feature reveals Netflix's content acquisition strategy — whether they prefer recent or older content.

---

##  Business Questions Answered

| # | Business Question |
|---|------------------|
| BQ1 | What is the overall split between Movies and TV Shows? |
| BQ2 | Is Netflix shifting strategy from Movies to TV Shows over time? |
| BQ3 | Which countries supply the most Netflix content? |
| BQ4 | What genres dominate the Netflix library? |
| BQ5 | How quickly does Netflix acquire content after release? |
| BQ6 | Which months does Netflix add the most content? |
| BQ7 | What is the rating distribution across content types? |
| BQ8 | Who are the most prolific directors on Netflix? |

---

##  Visualizations

- Movies vs TV Shows — count plot and pie chart
- Yearly content addition trend — line chart and proportional stackplot
- Top 10 countries — bar chart and stacked type breakdown
- Top 15 genres — horizontal bar chart
- Content acquisition age — histogram with KDE and cumulative percentage
- Monthly seasonality — stacked bar and total addition bar chart
- Rating distribution — overall and by content type
- Top 10 directors — horizontal bar chart
- Release year distribution — histogram with KDE

---

##  Key Findings

### 1. Netflix is shifting toward TV Shows
TV Show additions have grown significantly faster than Movies since 2018 — suggesting Netflix is investing in episodic content to improve subscriber retention and reduce churn.

### 2. USA dominates but India is rising
The United States supplies 35%+ of all Netflix content. India ranks second and growing rapidly — reflecting Netflix's aggressive push into South Asian markets post-2018.

### 3. International content is a key growth driver
International Movies and Dramas are the top genres in the library — confirming that non-English content is central to Netflix's global expansion strategy.

### 4. Netflix prioritizes recent content
The majority of content is acquired within 2 years of release — Netflix competes on recency, not archive depth. TV Shows are acquired even faster than Movies on average.

### 5. Q4 is peak content addition period
Netflix adds significantly more content in October–December — aligned with the holiday season when viewer hours spike. This is a deliberate subscriber retention strategy.

### 6. Netflix targets adult audiences
TV-MA is the most common rating — positioning Netflix against HBO/Showtime rather than Disney+ in the streaming wars. Mature content dominates both Movies and TV Shows.

### 7. International directors dominate top spots
The most prolific Netflix directors are predominantly from India and other international markets — reflecting long-term content partnerships with non-English creators.

---

##  Strategic Implications

| Finding | Implication |
|---------|-------------|
| TV Shows growing faster than Movies | Episodic content drives better retention than one-time movie views |
| India and South Korea emerging as content hubs | Netflix betting on international markets for subscriber growth |
| 60%+ content acquired within 2 years of release | Recency strategy — not a deep archive play |
| TV-MA dominates ratings | Adult subscriber focus, not family market |
| Q4 peak additions | Content strategy aligned with holiday viewing spikes |

---

##  How to Run

1. Clone the repository
2. Install dependencies:
```bash
pip install pandas matplotlib seaborn numpy
```
3. Place `netflix_titles.csv` in the same folder as the notebook
4. Open `netflix_analysis.ipynb` in Jupyter Notebook or VS Code
5. Run all cells

---

