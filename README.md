# Python_analysis-_project 

## Project Overview:
This project performs an Exploratory Data Analysis (EDA) on the Netflix Titles dataset to uncover insights about content trends, genre popularity, and country-wise production patterns.
It includes data cleaning, feature engineering, and visual storytelling using Seaborn and Matplotlib.

## ObjectivesUnderstand the distribution of Movies vs TV Shows on Netflix.
1. Analyze content growth trends over the years.
2. Identify top genres and top contributing countries.
3. Study release year distributions and content addition timelines.

## Tools & Libraries
1. Python
2. Pandas, NumPy for Data analysis & cleaning
3. Matplotlib, Seaborn, Plotly for Data visualization
4. Jupyter Notebook for Development and exploration environment

## Project Structure
### Install required libraries:
```python
import matplotlib.pyplot as plt
import pandas as pd
import seaborn as sns
import numpy as np
```
# Load dataset
```python
df = pd.read_csv(r"C:\Users\hp\Desktop\project\netflix_titles.csv")
df
```

## Data Overview & Quality Check
 1.View column names, data types, and non-null counts
```python 
df.info()
 ```
 2.Get statistical summary of numerical columns
 ```python
df.describe()
 ```
 3.Check dataset dimensions (rows, columns)
```python
df.shape
```
 4.Identify missing values in each column
```python
df.isnull().sum()
```
 5.Detect duplicate records
 ```python
df[df.duplicated()].shape
```


# Data Cleaning
1. Handle missing values
 ```python
df['director'] = df['director'].fillna('Unknown')
df['cast'] = df['cast'].fillna('Unknown')
df['country'] = df['country'].fillna('Unknown')
df['rating'] = df['rating'].fillna('Not Rated')
df['duration'] = df['duration'].fillna('Unknown')
```
2.Convert and clean date format
```python
df['date_added'] = pd.to_datetime(df['date_added'].str.strip(), errors='coerce', format='mixed')
```
3.Extract year and month from date
```python
df['year_added'] = df['date_added'].dt.year
```
```python
df['month_added'] = df['date_added'].dt.month
```
4.Remove rows where 'date_added' could not be parsed
```python
df.dropna(subset=['date_added'], inplace=True)
```

## Exploratory Data Analysis (EDA) & Visualization
After cleaning, the dataset was explored visually and statistically to understand the trends, patterns, and distributions within Netflix content:

1.**Initial Exploration**
 ```python
df.info()
df.describe(include='all')
df['type'].value_counts()
```

2.**Distribution of Movies vs TV Shows**
 ```python
plt.figure(figsize=(6,4))
sns.countplot(x='type', data=df, palette='Set2')
plt.title('Distribution of Movies vs TV Shows')
plt.xlabel('Type')
plt.ylabel('Count')
plt.show()
```

3.**Netflix Content Added by Year**
 ```python
plt.figure(figsize=(10,5))
df['year_added'] = df['year_added'].astype('Int64')  # ensure integer type
yearly = df['year_added'].value_counts().sort_index()

sns.lineplot(x=yearly.index, y=yearly.values, marker='o')
plt.title('Netflix Content Added by Year')
plt.xlabel('Year Added')
plt.ylabel('Number of Titles')
plt.show()
```

4.**Top 10 Countries with Most Netflix Titles**
 ```python
top_countries = df['country'].value_counts().head(10)
plt.figure(figsize=(10,5))
sns.barplot(x=top_countries.values, y=top_countries.index, palette='coolwarm')
plt.title('Top 10 Countries with Most Netflix Titles')
plt.xlabel('Number of Titles')
plt.ylabel('Country')
plt.show()
```

5.**Top 10 Most Common Netflix Genres**
 ```python
from collections import Counter
genre_list = df['listed_in'].str.split(', ')
genre_counts = Counter([g for sublist in genre_list for g in sublist])

top_genres = pd.DataFrame(genre_counts.most_common(10), columns=['Genre', 'Count'])

plt.figure(figsize=(10,5))
sns.barplot(x='Count', y='Genre', data=top_genres, palette='viridis')
plt.title('Top 10 Most Common Netflix Genres')
plt.show()
```

6.**Distribution of Release Years on Netflix**
 ```python
plt.figure(figsize=(12,6))
sns.histplot(df['release_year'], bins=40, kde=True)
plt.title('Distribution of Release Years on Netflix')
plt.xlabel('Release Year')
plt.ylabel('Number of Titles')
plt.show()
```

7.**Top 10 Countries: Movies vs TV Shows**
 ```python
country_type = df.groupby(['country', 'type']).size().unstack(fill_value=0)

top_country_type = country_type.sum(axis=1).sort_values(ascending=False).head(10)
top_country_type = country_type.loc[top_country_type.index]

top_country_type.plot(kind='bar', stacked=True, figsize=(10,6), colormap='coolwarm')
plt.title('Top 10 Countries: Movies vs TV Shows')
plt.xlabel('Country')
plt.ylabel('Number of Titles')
plt.legend(title='Type')
plt.show()
```

8.**Yearly Trend: Movies vs. TV Shows Added to Netflix**
 Create a DataFrame to analyze yearly growth by content type
 ```python
yearly_type_growth = df.groupby(['year_added', 'type']).size().unstack(fill_value=0)
yearly_type_growth = yearly_type_growth.loc[yearly_type_growth.index >= 2008] # Start from a relevant year

plt.figure(figsize=(12, 6))
sns.lineplot(data=yearly_type_growth['Movie'], label='Movies Added', marker='o', color='#E50914')
sns.lineplot(data=yearly_type_growth['TV Show'], label='TV Shows Added', marker='o', color='#00A8E1')
plt.title('Yearly Trend: Movies vs. TV Shows Added to Netflix')
plt.xlabel('Year Added')
plt.ylabel('Number of Titles')
plt.legend(title='Content Type')
plt.grid(axis='y', linestyle='--')
plt.show()
```

9.**'Distribution of Content Age When Added to Netflix**
 ```python
plt.figure(figsize=(10, 6))
sns.histplot(data=df, x='content_age_when_added', hue='type', 
             bins=30, kde=True, palette={'Movie': '#E50914', 'TV Show': '#00A8E1'}, 
             alpha=0.6)

plt.title('Distribution of Content Age When Added to Netflix')
plt.xlabel('Content Age (Years)')
plt.ylabel('Count of Titles')
plt.xlim(0, 30) # Limit x-axis for better focus on recent history
plt.legend(title='Type', labels=['TV Show', 'Movie'])
plt.show()
```



















 
 
