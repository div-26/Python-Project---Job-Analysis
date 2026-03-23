# Overview

This project explores the data analyst job market with a focus on the Indian landscape, using Python-based exploratory data analysis and visualization techniques.

The goal of this analysis is not just to extract insights, but to visually understand patterns in salary distribution, skill demand, and job trends. Through a series of visualizations, this project highlights how different skills influence salary outcomes and how demand for data roles evolves over time.

The dataset, sourced from Luke Barousse’s Python course, includes information on job titles, salaries, locations, and required skills. Using Python libraries such as Pandas, Matplotlib, and Seaborn, the analysis transforms raw job data into clear, interpretable visuals to support data-driven career insights.

## Questions Answered
Below are the questions answered in my project:

1. What are the skills most in-demand for the top 3 most popular data roles?
2. How are in-demand skills trending for Data Analysts in India?
3. How well do jobs and skills pay for Data Analysts in India?
4. What are the optimal skills for data analysts to learn? (High Demand AND High Paying)

## Tools I Used

For my deep dive into the data analyst job market, I used several key tools:

- **Python**: The backbone of my analysis, allowing me to analyze the data and find critical insights.I also used the following Python libraries:
    * Pandas Library: This was used to analyze the data.
    * Matplotlib Library: I visualized the data.
    * Seaborn Library: Helped me create more advanced visuals.
- **Jupyter Notebooks**: The tool I used to run my Python scripts which let me easily include my notes and analysis.
- **Visual Studio Code**: My go-to for executing my Python scripts.
- **Git & GitHub**: Essential for version control and sharing my Python code and analysis, ensuring collaboration and project tracking.

# Data Preparation & Cleanup

The dataset was prepared to ensure consistency and usability for analysis. This included:

- Converting date fields into appropriate datetime formats.
- Parsing skill-related data into structured lists for analysis  
- Filtering the dataset to focus on data analyst roles within the Indian job market

These steps ensured that the data was clean, structured, and suitable for exploratory analysis and visualization.

<details>
<summary>View data preparation code</summary>

```python
#importing libraries
import pandas as pd
import matplotlib.pyplot as plt
import ast
from datasets import load_dataset
import seaborn as sns

#loading the dataset
ds = load_dataset("lukebarousse/data_jobs")  

#converting to dataframe type                              
df = ds['train'].to_pandas()          

# job_posted_date cleanup
df['job_posted_date'] = pd.to_datetime(df['job_posted_date']) 

# job_skill cleanup
def clean_list(skill_list):
    if pd.notna(skill_list):
        return ast.literal_eval(skill_list)
    
df['job_skills'] = df['job_skills'].apply(clean_list)                       
```
</details>
<br>

# The Analysis
## 1. Exploratory Data Analysis
The objective of this section of the analysis was to explore the dataset to identify patterns in job roles, skill demand, and salary distributions before conducting deeper analysis.

### Key areas explored:
- Distribution of data roles based on job availability across the market 
- Geographic distribution of job opportunities across countries (excluding outliers to improve visual clarity)
- Companies with the highest number of job postings in data roles
- Prevalence of key job features such as remote work and benefits
- Distribution of Data Analyst roles across locations in India
- Companies with the highest hiring activity for Data Analyst roles in India
- Availability of key job features within Data Analyst roles in India

### Visualizations:
![Number of Jobs](Project/Assets/01.png)

![02](Project/Assets/01.2.png)

![03](Project/Assets/01.3.png)

![04](Project/Assets/01.4.png)

![05](Project/Assets/01.5.png)

![07](Project/Assets/01.7.png)

![06](Project/Assets/01.6.png)

### Key Insights

- The most common data roles are Data Analyst, Data Scientist, and Data Engineer  
- India shows a high concentration of job postings (excluding the U.S. as a significant outlier)  
- Emprego has the highest number of job listings, with over 6,000 postings  
- Most data roles do not consistently offer additional benefits such as remote work or health insurance  
- Hyderabad has the highest number of Data Analyst job opportunities within India  
- SAZ India and S&P Global are among the top hiring companies for data roles in India 


## 2. Most demanded skills across data roles
The objective here is to identify the most in-demand skills for the top 3 data roles to understand how skill requirements differ across roles.

I filtered the dataset to determine the most common data roles and extracted the top 5 most frequently required skills for each. This allows comparison of skill demand across roles and highlights key differences in required competencies.

### Visualizations:
![10](Project/Assets/02.png)
Bar graph visualizing the top 3 data roles and their top 5 skills associated with each.

### Key Insights:
- SQL is the most requested skill for Data Analysts and Data Scientists, with it in over half the job postings for both roles. For Data Engineers, Python is the most sought-after skill, appearing in 70% of job postings.
- Data Engineers require more specialized technical skills (AWS, Azure, Spark) compared to Data Analysts and Data Scientists who are expected to be proficient in more general data management and analysis tools (Excel, Tableau).
- Python is a versatile skill, highly demanded across all three roles, but most prominently for Data Scientists (72%) and Data Engineers (65%).

## 3. Skill demand trend for Data Analysts
In this section, I analyze how demand for key skills evolved over time to identify trends in the Data Analyst job market.

I filtered Data Analyst job postings and grouped skill occurrences by month. Calculated the top 5 most frequently requested skills for each month to track how demand changed throughout the year.

### Visualization
![11](Project/Assets/03.png)
Line chart showing the trend of top 5 skills for Data Analysts across the year 2023

### Key Insights
- SQL remains the most consistently demanded skill throughout the year, with a slight increase in relative demand toward the end of the year  
- Python is consistently the second most demanded skill, showing a gradual increase in demand over time  
- Excel maintains relatively stable demand, occasionally surpassing Python to become the second most requested skill  
- Tableau and Power BI show gradual upward trends, indicating increasing adoption despite lower overall demand  

## 4. Salary for data jobs in India
Here we analyze salary distributions across data roles and identify the highest-paying and most in-demand skills for Data Analysts.

I focused on job postings with available salary data. First examined salary distributions across major data roles to understand compensation patterns. Then narrowed the analysis to Data Analyst roles to compare high-paying skills with in-demand skills.

### Visualization
![12](Project/Assets/04_1.png)
The box plot above shows salary distributions across key data roles, highlighting differences in median salary and variation across positions.

### Key Insights
- Entry-level roles such as Data Analyst offer the lowest salary ranges, typically around $100K, with some positions extending up to $200K–$250K  
- Data Engineer and Data Scientist roles generally offer higher salaries than Senior Data Analyst roles, with typical ranges around $120K–$150K  
- Senior Data Scientist roles offer the highest compensation, followed closely by Senior Data Engineer positions, with typical salaries around $200K and top-end roles exceeding $300K 

## Highest Paid & Most Demanded skills for Data Analysts
Next, I narrowed my analysis and focused only on data analyst roles. I looked at the highest-paid skills and the most in-demand skills. I used two bar charts to showcase these.


### Visualization
![11](Project/Assets/04_2.png)
Two separate bar graphs visualizing the highest paid skills and most in-demand skills for data analysts in India.

### Key Insights
- Specialized tools such as PySpark, PostgreSQL, and GitLab are associated with the highest salaries, despite relatively lower demand  
- These specialized skills fall within a similar salary range, typically around $160K–$170K  
- Among the most in-demand skills, Power BI, Spark, and Tableau are linked to higher salary offerings, often exceeding $100K  
- Core skills such as SQL and Python, while highly demanded, are associated with comparatively lower salary ranges of approximately $90K–$100K
- Skills such as R, AWS, and Oracle are associated with lower salary ranges, typically below $80K, indicating that not all technical skills command high compensation

## 5. Most Optimal Skills for Data Analysts in India
Finally I identified the most valuable skills by combining demand and salary to determine which skills offer the best return in the job market.

I calculated the percentage of job postings requiring each skill and compared it with the median salary associated with those skills. This allows identification of skills that are both highly demanded and well-compensated.

### Visualizations
![11](Project/Assets/05_1.png)
The scatter plot above maps skill demand against median salary, highlighting the most optimal skills based on their position in the top-right region (high demand, high pay).

### Key Insights
- Skills such as PowerPoint, Spark, and Looker are associated with higher salaries but appear less frequently in job postings, indicating niche but well-compensated roles  
- Skills like Oracle, AWS, and R show lower demand and lower salary ranges within Data Analyst roles, suggesting they may be more valuable in specialized roles such as Data Engineering  
- Core skills including SQL, Python, and Excel demonstrate both high demand and stable compensation, making them foundational for building a career in data analysis  

## Visualizing different technologies
Then I extended the analysis by grouping skills into broader technology categories (e.g., programming, databases, visualization tools) to understand how different domains compare in terms of demand and compensation.

### Visualization
![12](Project/Assets/05_2.png)
A scatter plot visualizing the most optimal skills (high paying & high demand) for data analysts in India with color labels for technology.

### Key Insights
- Analyst tools and libraries are associated with higher salary ranges but lower demand, indicating niche and specialized use cases  
- Programming skills show the highest overall demand (with exceptions such as R), but do not consistently offer the highest salaries for Data Analyst roles  
- Cloud technologies exhibit relatively lower demand and lower salary ranges within Data Analyst roles  

# Key Takeaways

This project strengthened both my understanding of the data analyst job market and my ability to work with real-world datasets using Python.

- Developed practical experience in data manipulation and visualization using Pandas, Matplotlib, and Seaborn  
- Reinforced the importance of data cleaning and preprocessing for accurate analysis  
- Gained insight into how skill demand, salary, and job availability interact within the data job market  


## Market Insights
- High-paying skills are not always the most in-demand, highlighting a trade-off between employability and earning potential  
- Foundational skills such as SQL, Python, and Excel remain essential due to their consistent demand  
- Specialized tools and technologies can command higher salaries but are typically required less frequently  
- Skill demand trends evolve over time, emphasizing the need for continuous learning  



## Challenges
- Handling missing and inconsistent data required careful preprocessing to maintain data quality  
- Designing clear and effective visualizations was challenging but essential for communicating insights  
- Balancing depth of analysis with overall clarity required focusing on the most impactful findings  


# Conclusion

This project demonstrates how data analysis and visualization can be used to extract meaningful insights from job market data. By combining exploratory analysis with visual storytelling, it highlights key patterns in skill demand, salary trends, and career opportunities within the data analyst domain.

The findings reinforce the importance of building a balanced skill set that includes both foundational and specialized tools. As the job market continues to evolve, ongoing analysis and adaptability will remain critical for long-term success in data analytics.
