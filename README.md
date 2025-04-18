
# The Analysis

## 1. What are the most demanded skills for the top 3 most popular data roles?

To identify the top skills in demand, I analyzed job postings from a dataset focused on data-related roles in the U.S. I filtered the data by the top three most common job titles and visualized the five most frequently mentioned skills for each using horizontal bar plots. The visualizations show the likelihood of each skill appearing in job postings, helping highlight which technical abilities are most valued across roles succh as Data Analyst, Data Engineer, and Data Scientist.

Here is the link to my notebook to see a detailed breakdown of the steps taken: [2_Skills_Demand.ipynb](3_Project\2_Skills_Demand.ipynb)


### Code

```python

fig, ax = plt.subplots(len(job_titles), 1)

sns.set_theme(style='ticks')

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
    sns.barplot(data=df_plot, x='skill_percent', y='job_skills', ax=ax[i], hue='skill_count', palette='dark:b_r')
    ax[i].set_title(job_title)
    ax[i].set_ylabel('')
    ax[i].set_xlabel('')
    ax[i].get_legend().remove()
    ax[i].set_xlim(0, 78)


    for n, v in enumerate(df_plot['skill_percent']):
        ax[i].text(v + 1, n, f'{v:.0f}%', va='center')

    
    if i != len(job_titles) - 1: 
        ax[i].set_xticks([])

fig.suptitle('Likelihood of Skills Requested in US Job Postings', fontsize=15)
fig.tight_layout(h_pad=.8)
plt.show()

```

### Visualization

![Visualization of Top Skills for Top 3 Data Roles](3_Project\Images\skill_demand_for_data_jobs.png)


### Insights

**Skill-Specific Insights:**

* **SQL is highly valued across all three roles:** It is the most frequently requested skill for **Data Analysts (51%)** and **Data Engineers (68%)**, and the second most requested for **Data Scientists (51%)**. This underscores the fundamental importance of database interaction, querying, and management in data-related fields.

* **Python is a highly demanded skill for both Data Engineers and Data Scientists:** It is the top requested skill for **Data Scientists (72%)** and the second most requested for **Data Engineers (65%)**. It also has a significant presence in **Data Analyst** roles (**27%**), indicating the importance of programming along with data manipulation, analysis, and modeling to perform data-related tasks.

**Role-Specific Insights:**

* **Data Analyst:** Requires skills in data manipulation (**SQL**, **Excel**) and data visualization (**Excel**, **Tableau**). Some programming/scripting knowledge (**Python**, **SAS**) would also be beneficial. The focus seems to be on extracting, cleaning, analyzing, and presenting data insights.

* **Data Engineer:** Demands skills in data manipulation (**SQL**), programming (**Python**), cloud technologies (**AWS**, **Azure**), and big data technologies (**Spark**). The focus seems to be on using data infrastructure and processing skills to build and maintain data pipelines.

* **Data Scientist:** Seeks skills in programming (**Python**, **R**), data manipulation (**SQL**), and statistical analysis (**R**, **SAS**). Some skills in data visualization (**Tableau**) would also be notable. The focus seems to be on building predictive models and extracting complex insights.


## 2. How are in-demand skills trending for Data Analysts?

To understand how demand for specific skills has evolved, I tracked the top five most requested skills for Data Analyst roles over time. Using a line plot, I visualized trends in the likelihood of each skill appearing in U.S. job postings throughout 2023. This analysis provides insight into which skills are gaining or losing popularity, helping job seekers align their learning with current industry needs.

Here is the link to my notebook to see a detailed breakdown of the steps taken: [3_Skills_Trend.ipynb](3_Project\3_Skills_Trend.ipynb)


### Code

```python

df_plot = df_DA_US_percent.iloc[:, :5]
sns.lineplot(data=df_plot, dashes=False, legend='full', palette='tab10')
sns.set_theme(style='ticks')
sns.despine()

plt.title('Trending Top Skills for Data Analysts in the US')
plt.ylabel('Likelihood in Job Posting')
plt.xlabel('2023')
plt.legend().remove()

from matplotlib.ticker import PercentFormatter
ax=plt.gca()
ax.yaxis.set_major_formatter(PercentFormatter(decimals=0)) # Getting rid of the decimal

for i in range(5):
    plt.text(11.2, df_plot.iloc[-1, i], df_plot.columns[i])

plt.show()


```

### Visualization
![Top Trending Skills for Data Analyst in the US](3_Project\Images\skills_trending_for_data_analyst.png)

### Insights

* **SQL consistently remains the most in-demand skill:**  Throughout the year, **SQL** has had the highest likelihood of being requested in Data Analyst job postings, generally hovering above the 55% mark and only dipping slightly towards the end of the year. This reinforces **SQL's** fundamental importance for data analysis roles.

* **Excel ia a consistently important skill, but with fluctuations:** **Excel** consistently ranks as the second most requested skill. However, its demand showed more variability throughout the year, with a notable peak around July and August and then declining before rising again towards the end of the year.

* **Python and Tableau exhibit a generally upward trend:** Both **Python** and **Tableau** showed a tendency to be requested more frequently as the year progressed, suggesting their growing relevance in the Data Analyst skillset. **Tableau** showed a particularly noticeable increase in the later months.

* **Power BI shows relatively stable but lower demand:** **Power BI** consistently had the lowest likelihood of being requested among the skills presented, with relatively minor fluctuations throughout the year. **Power BI** generally remains in the 20-25% range.

## 3. How well do jobs and skills pay for Data Analysts?



Here is the link to my notebook to see a detailed breakdown of the steps taken: [.ipynb](3_Project\4_Salary_Analysis.ipynb)


### Code

```python



```

### Visualization
![]()

### Insights


## 4. What is the most optimal skill to learn for Data Analysts?



Here is the link to my notebook to see a detailed breakdown of the steps taken: [.ipynb](3_Project/5_Optimal_Skills.ipynb)


### Code

```python



```

### Visualization
![]()

### Insights


