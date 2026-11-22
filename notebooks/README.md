# 📓 Notebooks

Run these notebooks in order. Each one loads the [`lukebarousse/data_jobs`](https://huggingface.co/datasets/lukebarousse/data_jobs) dataset from Hugging Face and does its own cleanup, so you can also open any notebook on its own.

| # | Notebook | Question Answered | Key Output |
|---|----------|-------------------|------------|
| 1 | [1_EDA_Intro.ipynb](1_EDA_Intro.ipynb) | What does the data job market look like? (roles, countries, companies, job opportunities) | Exploratory charts of the dataset |
| 2 | [2_Skill_Demand.ipynb](2_Skill_Demand.ipynb) | What are the most demanded skills for the top 3 most popular data roles? | Likelihood of skills requested per role |
| 3 | [3_Skills_Trend.ipynb](3_Skills_Trend.ipynb) | How are in-demand skills trending for Data Analysts? | Monthly trend of top 5 skills in 2023 |
| 4 | [4_Salary_Analysis.ipynb](4_Salary_Analysis.ipynb) | How well do jobs and skills pay for Data Analysts? | Salary distributions, top-paid vs. most-demanded skills |
| 5 | [5_Optimal_Skills.ipynb](5_Optimal_Skills.ipynb) | What are the optimal skills to learn? (high demand **and** high pay) | Demand vs. median salary scatter, colored by technology |

## 🔧 Common Setup Used in Every Notebook

```python
import ast
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
from datasets import load_dataset

dataset = load_dataset('lukebarousse/data_jobs')
df = dataset['train'].to_pandas()

df['job_posted_date'] = pd.to_datetime(df['job_posted_date'])
df['job_skills'] = df['job_skills'].apply(lambda x: ast.literal_eval(x) if pd.notna(x) else x)
```

⬅️ Back to the [main README](../README.md) for the full write-up, charts, and insights.
