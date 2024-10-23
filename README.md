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
- SQL Dominance: SQL remains the most sought-after skill in data analysis, with a consistent demand of over 50% throughout the year. This indicates its foundational role in most data-related tasks.

- Excel's Steady Decline: While Excel is still popular, its demand has steadily declined, especially from mid-2023, dropping from approximately 45% to just below 35% by the end of the year.

- Python's Importance: Python remains a critical skill, fluctuating around the 30% range but dipping slightly towards the latter half of the year. Its utility in data analysis and machine learning maintains its relevance.

- Tableau's Consistent Demand: Tableau, used for data visualization, has maintained a steady demand at around 25-30%, showing that data presentation tools remain essential in the data analysis field.

- SAS Declining: SAS, which was less demanded compared to other tools, shows a slight rise in the final quarter of the year, yet still remains the least requested among the top five skills, with a demand of about 20%.

- Seasonal Changes in Demand: A notable trend is that there are peaks and drops around the mid-year period for skills like Python and Tableau, possibly reflecting specific projects or seasonal hiring trends in the data analysis industry.

# The Analysis

## 3. How well do jobs and skills pay for Data Analysts?

### Salary Analysis 

#### Visualize Data

```python
sns.boxplot(data=df_US_top6, x='salary_year_avg', y='job_title_short', order=job_order)
sns.set_theme(style='ticks')

plt.title('Salary Distribution in the United States')
plt.xlabel('Yearly Salaty ($USD)')
plt.ylabel('')
plt.xlim(0, 600000)
ticks_x = plt.FuncFormatter(lambda y, pos: f'${int(y/1000)}K')
plt.gca().xaxis.set_major_formatter(ticks_x)
plt.show()
```

#### Results

![Salary Distribution od Data Jobs in the US](./images/Salary%20Distribution%20in%20United%20States.png)
*Box plot visualizing the salary distributions for the tip 6 data job titles.*

#### Insights: 

- Senior Data Scientist and Senior Data Engineer positions have the highest median salaries, both above $150K, and they show a wide distribution of salaries with a significant number of outliers, some reaching close to $600K.

- Data Scientist and Data Engineer roles have similar salary distributions with median salaries around $120K, but with fewer extreme outliers compared to their senior counterparts.

- Senior Data Analyst salaries also have a median of around $100K, but the range of salaries is narrower compared to the other senior-level roles.

- Data Analyst is the lowest-paying role among the positions, with a median salary below $100K and a narrower distribution overall.

- Most roles exhibit a wide range of outliers, indicating that while the majority of professionals earn within a certain range, some individuals can earn significantly more, particularly in senior positions.

# The Analysis
## 3. How well do jobs and skills pay for Data (...)
### Highest Paid & Most Demanded Skills for Data Analysts
#### Visualize Data

```python
fig, ax = plt.subplots(2, 1)

# Top 10 Highest Paid Skills for Data Analysts
sns.barplot(data=df_DA_top_pay, x='median', y=df_DA_top_pay.index, hue='median', ax=ax[0], palette='dark:b_r')

# Top 10 Most In-Demand Skills for Data Analysts
sns.barplot(data=df_DA_skills, x='median', y=df_DA_skills.index, hue='median', ax=ax[1], palette='light:b')
```

### Result

![Top 10 Highest Paid Skills For Data Analysts](./images/Top%2010%20Highest%20Paid%20Skills%20For%20Data%20Analysts.png)

#### Insights:
`Top 10 Highest Paid Skills for Data Analysts:`

* The top-paying skills for Data Analysts are primarily technical and involve advanced platforms and tools, such as dplyr, bitbucket, and gitlab, which are popular in the data science and software development ecosystems.

* Emerging technologies like hugging face (used for AI models), solidity (for blockchain development), and couchbase (for distributed databases) command high salaries, with median salaries exceeding $125K.

* The highest-paying skill, dplyr, is a popular tool for data manipulation in R programming, which reflects the growing demand for specialized data manipulation capabilities.

* Cloud and distributed computing skills, such as cassandra, vmware, and mxnet, are also highly compensated, with median salaries approaching $150K.

* Though these are the top-paid skills, there is only few job postings about each of them.

`Top 10 Most In-Demand Skills for Data Analysts:`

* Python is the most in-demand skill for Data Analysts, indicating its dominant role in data analysis and machine learning workflows.

* Tableau and R are also highly sought-after skills, demonstrating the need for strong data visualization and statistical analysis capabilities in Data Analyst roles.

* Traditional database systems like SQL server and tools like SAS are still highly valued, showing that while new technologies are emerging, core skills in handling databases and statistical software remain essential.

* Excel, Powerpoint, and Word rank among the top 10 in-demand skills, highlighting the continued relevance of fundamental office tools for data reporting and presentation in business environments.

# The Analysis

## 4. What is the most optimal skill to learn for Data Analysts?

#### Visualize Data

```python
sns.scatterplot(
    data=df_plot,
    x='skill_percent',
    y='median_salary',
    hue='techology'
)

sns.set_theme(style='ticks')
texts = []
for i, txt in enumerate(df_DA_skills_high_demand.index):
    texts.append(plt.text(df_DA_skills_high_demand['skill_percent'].iloc[i], df_DA_skills_high_demand['median_salary'].iloc[i], txt))


adjust_text(texts, arrowprops=dict(arrowstyle='->', color='gray'))


plt.xlabel('Percent of DA jobs', fontweight='bold', labelpad=15)
plt.ylabel('Median Yearly Salary', fontweight='bold', labelpad=15)
plt.title(f'Most Optimal Skills for Data Analysts in the US', fontweight='bold')


ax = plt.gca()
ax.yaxis.set_major_formatter(plt.FuncFormatter(lambda y, pos: f'${int(y/1000)}K'))
ax.xaxis.set_major_formatter(PercentFormatter(decimals=0))


plt.tight_layout()
plt.show()
```
#### Results

![Most Optimal Skills for Data Analysts in the US](./images/Most%20Optimal%20Skills%20for%20Data%20Analysts.png)

*Scatter plot visualizing optimal skills to learn as a DA.* 
#### Insights:
* Oracle and Python are among the top skills in terms of median yearly salary, reaching around $96K to $98K. These skills are highly valued, especially for cloud computing (Oracle) and programming (Python), which are essential in data analysis and data science fields.

* SQL Server and Tableau also command high salaries, around $92K, indicating that databases and visualization tools are critical for data analysts.

* SQL stands out as the skill with the highest percent of DA jobs (about 55%), which shows how frequently it is required in the data analysis job market. Despite the high demand, the salary for SQL knowledge is around $92K, slightly lower than Oracle and Python.

* Excel is also quite prevalent in about 40% of data analyst jobs, but it commands a lower salary of around $85K, suggesting that while Excel is widely used, it may not be as highly compensated compared to more specialized tools like SQL or Tableau.

* Power BI, PowerPoint, and Word represent common analyst tools, with relatively lower salaries (ranging from $82K to $90K). These are more general tools often used for reporting and presentations, making them essential but not necessarily the highest-paying.

* On the other hand, programming languages like Go and Python have higher salaries. This suggests that programming skills are more specialized and likely associated with more complex tasks, hence leading to higher compensation.

* The dominance of SQL in job postings highlights the importance of database management skills in the data analyst role. Similarly, Tableau and Power BI are widely used tools for data visualization, making them key skills for effective data communication.

