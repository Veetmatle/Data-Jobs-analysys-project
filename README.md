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