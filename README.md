# Project-Analyzing-Students-Mental-Health
Does going to university in a different country affect your mental health? A Japanese international university surveyed its students in 2018 and published a study the following year that was approved by several ethical and regulatory boards.

The study found that international students have a higher risk of mental health difficulties than the general population, and that social connectedness (belonging to a social group) and acculturative stress (stress associated with joining a new culture) are predictive of depression.

Explored the students data using PostgreSQL to find out if you would come to a similar conclusion for international students and see if the length of stay is a contributing factor.

# Query

Query 1:
```sql
SELECT * 
FROM students;
```

Query 2:
```sql
SELECT stay, COUNT(inter_dom) AS count_int, ROUND(AVG(todep),2) AS average_phq, ROUND(AVG(tosc),2) AS average_scs, ROUND(AVG(toas),2) AS average_as
FROM students
WHERE inter_dom = 'Inter'
GROUP BY stay
ORDER BY stay DESC
LIMIT 9;
```

# My Step-by-Step Explanation of the Query:

SELECT Clause:
SELECT stay, COUNT(inter_dom) AS count_int, ROUND(AVG(todep),2) AS average_phq, ROUND(AVG(tosc),2) AS average_scs, ROUND(AVG(toas),2) AS average_as

stay: Represents the length of stay of the students, which is the primary factor being analyzed.

COUNT(inter_dom) AS count_int: Calculates the number of international students for each length of stay and aliases it as count_int.

ROUND(AVG(todep), 2) AS average_phq: Computes the average PHQ-9 test scores for each length of stay, rounded to two decimal places, and aliases it as average_phq.

ROUND(AVG(tosc), 2) AS average_scs: Computes the average SCS test scores for each length of stay, rounded to two decimal places, and aliases it as average_scs.

ROUND(AVG(toas), 2) AS average_as: Computes the average ASISS test scores for each length of stay, rounded to two decimal places, and aliases it as average_as.

FROM Clause:
FROM students

Specifies the students table as the source of the data.

WHERE Clause:
WHERE inter_dom = 'Inter'

Filters the records to include only international students. The condition inter_dom = 'Inter' ensures that only rows where the inter_dom column has the value 'Inter' are considered.

GROUP BY Clause:
GROUP BY stay

Groups the records by the stay column. This means that all the records with the same length of stay will be aggregated together.

ORDER BY Clause:
ORDER BY stay DESC

# How the Query Solves the Business Question?

The business question asks us to explore how the length of stay impacts the average mental health diagnostic scores of international students. My query addresses this by:

Filtering for International Students: The WHERE inter_dom = 'Inter' clause ensures that only international students are included in the analysis.

Grouping by Length of Stay: The GROUP BY stay clause aggregates the data by the length of stay, allowing us to see how the average scores change with different lengths of stay.

Calculating Averages: The AVG functions calculate the mean scores for the PHQ-9, SCS, and ASISS tests, providing insights into the mental health status of students for each length of stay.

Counting Students: The COUNT(inter_dom) AS count_int clause gives us the number of students in each length of stay group, which helps in understanding the sample size for each category.

Ordering and Limiting Results: The ORDER BY stay DESC clause ensures that the results are sorted by length of stay in descending order, and the LIMIT 9 clause restricts the output to the top 9 lengths of stay, making the results more manageable and focused on the most significant categories.

Orders the results by the stay column in descending order. This means that records with the longest stay will appear first.

LIMIT Clause:
LIMIT 9;

Limits the number of rows returned by the query to 9. This ensures that the output table has only nine rows.

# What is the Order of Execution?

1. FROM: Identifies the source table (students).
2. WHERE: Filters rows to include only international students.
3. GROUP BY: Groups the filtered rows by stay.
4. SELECT: Selects and calculates the specified columns.
5. ORDER BY: Sorts the results by stay in descending order.
6. LIMIT: Limits the result set to 9 rows.

This logical sequence ensures that the data is filtered, grouped, aggregated, sorted, and then limited to produce the final result set.

# Key Observations:

Length of Stay and Mental Health:

PHQ-9 (Depression): The average depression scores (PHQ-9) are generally lower for students with a longer stay, which may suggest that students with more extended periods at the university experience fewer symptoms of depression. For example, students with a 10-year stay have an average PHQ-9 score of 13, whereas students with a 1-year stay have an average score of 7.48.

SCS (Social Connectedness): The average social connectedness scores (SCS) tend to be higher for students with a shorter stay, indicating that students who have recently arrived may feel more socially connected initially. However, this score stabilizes for longer stays.

ASISS (Acculturative Stress): Acculturative stress decreases with longer stays. For instance, students with a 10-year stay have a lower average ASISS score (50) compared to those with a 1-year stay (72.8), indicating that students may adapt better over time, reducing their stress levels associated with joining a new culture.
Student Count and Distribution:

There is a significant number of international students in their first year (95 students), which drops sharply in subsequent years, with only 1 student at the 10-year mark. This could imply either high attrition or a natural reduction as students graduate or return home.

# Key Insight:

The findings suggest that longer stays at the university generally correlate with better mental health outcomes for international students, particularly in terms of reduced depression and acculturative stress. However, initial high levels of social connectedness tend to taper off over time, possibly as students integrate more fully into the university community.

# Strategic Recommendations:

Support Programs for New Arrivals:

Implement targeted support programs focusing on maintaining social connectedness and addressing acculturative stress, particularly for students in their first few years.
Long-Term Integration Efforts:

Develop long-term mental health and wellness programs that support students as they continue their studies, helping them manage stress and maintain social connections.
Monitoring and Continuous Assessment:

Regularly monitor the mental health of international students throughout their stay, with tailored interventions as necessary based on the length of stay.
Mentorship and Peer Support:

Establish mentorship programs pairing newer students with those who have been at the university longer, facilitating smoother transitions and sustained social connections.
This analysis not only confirms the initial hypothesis that international students face mental health challenges but also emphasizes the importance of continuous support throughout their academic journey, with particular attention to their length of stay.
