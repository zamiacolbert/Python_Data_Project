
# The Analysis

## What are the most demanded skills for the top 3 most popular data roles?

To identify the top skills in demand, I analyzed job postings from a dataset focused on data-related roles in the U.S. I filtered the data by the top three most common job titles and visualized the five most frequently mentioned skills for each using horizontal bar plots. The visualizations show the likelihood of each skill appearing in job postings, helping highlight which technical abilities are most valued across roles like Data Analyst, Data Engineer, and Data Scientist.

Here is the link to my notebook to see a detailed breakdown of the steps taken: [2_Skill_Demand.ipynb](3_Project\2_Skills_Demand.ipynb)


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

Overall Observations:

## Likelihood of Skills Requested in US Job Postings

This data visualizes the likelihood (in percentage) of specific skills being requested in job postings for three prominent data-related roles in the US: Data Analyst, Data Engineer, and Data Scientist.

**Skill-Specific Insights:**

* **SQL is a foundational skill across all roles:** It is the most frequently requested skill for **Data Analysts (51%)** and **Data Engineers (68%)**, and the second most requested for **Data Scientists (51%)**. This underscores the fundamental importance of database interaction in the data field.
* **Python is crucial for advanced data roles:** It is the top requested skill for **Data Scientists (72%)** and the second most requested for **Data Engineers (65%)**. It also has a significant presence in **Data Analyst** roles (**27%**), indicating its growing importance for data manipulation and analysis.
* **Cloud technologies are vital for Data Engineers:** Both **AWS (43%)** and **Azure (32%)** are frequently mentioned in **Data Engineer** job postings, highlighting the reliance on cloud platforms for data infrastructure.
* **Data Analysts focus on visualization and data manipulation:** **Excel (41%)** and **Tableau (28%)** are prominent skills for **Data Analysts**, emphasizing the need to communicate data insights effectively.
* **Statistical software is key for Data Scientists:** **R (44%)** and **SAS (24%)** are important skills for **Data Scientists**, reflecting the need for statistical modeling and analysis expertise.
* **Big Data processing is relevant for Data Engineers:** **Spark (32%)** is a requested skill for **Data Engineers**, indicating the need to handle and process large datasets.

**Role-Specific Insights:**

* **Data Analyst:** Strong emphasis on data querying (**SQL**), spreadsheet software (**Excel**), data visualization (**Tableau**), and some scripting/statistical skills (**Python**, **SAS**).
* **Data Engineer:** Core skills revolve around data infrastructure and pipelines, including database management (**SQL**), programming (**Python**), and cloud platforms (**AWS**, **Azure**), as well as big data technologies (**Spark**).
* **Data Scientist:** Focus on advanced analytical and modeling skills, with a strong need for programming (**Python**, **R**), statistical software (**R**, **SAS**), and data querying (**SQL**). Visualization skills (**Tableau**) are also relevant.



