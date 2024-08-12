# Project-Analyzing-Students-Mental-Health
Does going to university in a different country affect your mental health? A Japanese international university surveyed its students in 2018 and published a study the following year that was approved by several ethical and regulatory boards.

The study found that international students have a higher risk of mental health difficulties than the general population, and that social connectedness (belonging to a social group) and acculturative stress (stress associated with joining a new culture) are predictive of depression.

Explored the students data using PostgreSQL to find out if you would come to a similar conclusion for international students and see if the length of stay is a contributing factor.

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
