# python_analysis-_project 

## Project Overview:
This project performs an Exploratory Data Analysis (EDA) on the Netflix Titles dataset to uncover insights about content trends, genre popularity, and country-wise production patterns.
It includes data cleaning, feature engineering, and visual storytelling using Seaborn and Matplotlib.

## ObjectivesUnderstand the distribution of Movies vs TV Shows on Netflix.
1.Analyze content growth trends over the years.
2.Identify top genres and top contributing countries.
3.Study release year distributions and content addition timelines.

## Tools & Libraries
 Python
1.Pandas, NumPy for Data analysis & cleaning
2.Matplotlib, Seaborn, Plotly for Data visualization
3.Jupyter Notebook for Development and exploration environment

## Project Structure
**Install required libraries**:
```python
import matplotlib.pyplot as plt
import pandas as pd
import seaborn as sns
import numpy as np
```
**Load dataset**
```python
df = pd.read_csv(r"C:\Users\hp\Desktop\project\netflix_titles.csv")
df
```

**Data Overview & Quality Check**
 1.View column names, data types, and non-null counts
```python df.info() ```
 2.Get statistical summary of numerical columns
 ```pythondf.describe() ```
 3.Check dataset dimensions (rows, columns)
```python df.shape  ```
 4.Identify missing values in each column
```python df.isnull().sum()```
 5.Detect duplicate records
 ```pythondf[df.duplicated()].shape ```

**Data cleaning**





 
 
