# The Analysis 

## 1. What are the most demanded skills for the top 3 most popular data roles?

To find the most in demand skills for the top 3 most popular data roles, I filtered out those positions by which ones were the most popular , and got the top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills , showing which skills I should pay attention to depending on the role I am targeting 


View my notebook with deetailed steps here :
[skills_demand.ipynb](skills_demand.ipynb)

### Visualize Data

```python 
fig , ax = plt.subplots(len(job_titles), 1)

sns.set_theme(style='ticks')

for i, job_title in enumerate(job_titles):
     df_plot = df_skills_percent[df_skills_percent['job_title_short']==job_title].head(5)
     #df_plot.plot(kind='barh',x='job_skills',y='skill_percent',ax=ax[i],title=job_title)
     sns.barplot(data=df_plot,x='skill_percent',y='job_skills',ax=ax[i],hue='skill_count',palette='dark:b_r')
     ax[i].set_title(job_title)
     ax[i].set_ylabel('')
     ax[i].set_xlabel('')
     ax[i].get_legend().remove()
     ax[i].set_xlim(0,70)

     for n,v in enumerate(df_plot['skill_percent']):
          ax[i].text(v + 1, n , f'{v:.0f}%',va='center')
     
     if i != len(job_titles)-1:
          ax[i].set_xticks([])



fig.suptitle(f'Likelihood of Skills Requested in {country} Job Postings', fontsize=13)
fig.tight_layout(h_pad=0.5)
plt.show()

```


### Results

![Visualization of the Top SKills for Top Roles](images\skills_demand.png)


### Insights

- Python is the most requested skill , highly demand across all three roles, but most promimently for Data Scientists(67%) and Data Engineers(57%).
- SQL is the most requested skill for Data Analysts and Data Engineers , with it in over half the job postings for both roles. 
- Data Engineers and Data Scientists require more specialized technicals skills (AWS, Azure, Spark, SAS) compared to Data Analysts who are expected to be more proficient in more general data management and analysis tools (Excel, tableau)