# The Analysis - my exercise

## 1. What are the most demanded skills for the top 3 most popular data roles?

To find the most demanded skills for the top 3 most popular data roles I filtered out those positions by which ones were the most popular, and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills I should learn in order to become a decent Data Analyst or who knows maybe AI specialist later :D

My detailed notebook insights: [4P_EDA_Intro.ipynb](4P_EDA_Intro.ipynb)

### Code for visualisation of Likelihood of Skills Requested in US Job Postings

```python
fig, ax = plt.subplots(len(job_titles), 1, figsize=(8, len(job_titles) * 2))

sns.set_theme(style='ticks')

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
    sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:g_r')

    ax[i].set_ylabel("")
    ax[i].set_title(job_title, fontweight='bold')
    ax[i].set_xlim(0, 78)
    ax[i].get_legend().remove()
    ax[i].legend().set_visible(False)
    ax[i].set_xlabel("")
```
 
 ### Result of the provided code:

 ![Visualisation](./images/Likelihood%20of%20Skills%20Requested%20in%20US%20Job%20Postings%20chart.png)

 ### Insights:

 - `Python` seems to be a decent, demanded skill to learn, mostly for **Data Scientists** `(72%)` and **Data Engineers** `(65%)`.
 - `SQL` is the most demanded skill almost for every role, which is a clear sign of importance of that skill.
 - **Data Engineers** require more specialized technical skills (AWS, Azure) compared to Data Analysts and Data Scientists who are expected to be proficient in more general data management and analysys tools.
 - Profitable **Data Scientist** skill to learn may be `R language - (44%)`, as it is easy to learn and provides several options as well.

## 2. How are in-demand skills trending for Data Analysts?

## Visualize Data
```python
sns.lineplot(data=df_plot, dashes=False, palette='tab10')
sns.set_theme(style='ticks')
sns.despine()

plt.title('Trending Top Skills for Data Analysys in US', fontweight='bold')
plt.ylabel('Likelihood in Job Posting', fontweight='bold', labelpad=20) 
plt.xlabel('2023', fontweight='bold', labelpad=15)  
plt.legend(title='Job Skills')

from matplotlib.ticker import PercentFormatter
ax = plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(decimals=0))

plt.show()
```

### Results
![Trending Top Skills for Data Analysts in the US](./images/Trending%20top%20skills%20for%20data%20analysts%20in%20US.png)

*Line graph visualizating the trending top skills for data analysts in the US in 2023.*

### Insights:
- SQL consistently remains the top skill requested in job postings for data analysis throughout 2023, maintaining a likelihood above 55%.
- Python follows closely as the second most sought-after skill, with a steady trend around 50% of job postings, showing some slight decrease mid-year but stabilizing towards the end of the year.
- R has a lower likelihood, ranging between 25% to 30%, and experiences a noticeable drop between August and October, but slightly recovers towards the end of the year.
- Tableau and Excel are the least requested skills among the five, with both hovering around 20% throughout the year, showing minimal fluctuation.
- There seems to be more volatility in R skill demand compared to the others, suggesting changes in preferences or job requirements for this specific skill.