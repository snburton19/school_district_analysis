# School District Analysis - Module 4 Challenge
<sub>Chapel Hill - Data Science Bootcamp</sub>

## Overview of Project
For Module 4, Pandas - a Python library created for data analysis and manipulation - was used to examine data collected from a school district's high schools. For each student in the district, their name, ID, grade, reading score, math score, school name, school type (public versus private), and school budget were given. With the provided information, the goal was to clean, summarize, drill down into, and compare the data to discover budget- and score-related patterns within the school district.

## Results
* Preparing and Cleaning the Data
  * All rows with null values were dropped, as were all duplicated rows.

![Null values in the dataset](/images/sum_null.png)
![Number of duplicated rows](/images/sum_duplicated.png)

  * Because the original dataset's grade column set each grade as 9th, 10th, 11th, or 12th, the "th" was dropped from each cell in the column, and the column's data type was changed from object to integer to allow for easier data manipulation.

![Original data types](/images/dtypes_original.png)
![Modified data types](/images/dtypes_modified.png)

* Summarizing the Data
  * Using the Pandas describe function, the mean, standard deviation, minimum, maximum, and quartiles were calculated for the `student_id`, `grade`, `reading_score`, `math_score`, and `school_budget` columns.

![Summary statistics](/images/describe.png)

* Drilling Down into the Data - Reading and Math Scores
  * Using the `loc` and `iloc` functions, the data was manipulated to show subsets of the data - such as the summary statistics(using the describe function) of ninth graders in the district and viewing the reading scores of one specific school.

![Ninth grade summary statistics](/images/describe_grade9.png)
![Dixon High School's reading scores](/images/dixon_reading.png)

* Comparing the Data - Charter vs. Public Schools
  * Using the Pandas `groupby` function, the average school budget for all charter schools and public schools in the district were calculated.

![Average budget per school type](/images/school_type_budget.png)
  * Using `groupby`, `count`, and `sort_values`, the data was grouped to count the total number of students per school, and sorted in descending order.

![Student count per school](/images/student_count.png)
  * Using `groupby` and `mean`, schools in the district were sorted into charter versus public and further separated by grade, to show the average math score of each grade for charter and public schools.

![Charter and public math scores by grade](/images/school_type_grade_math_score.png)

## Summary
From the current level of analysis done on the data, several conclusions can be made. Across all schools in the dataset, the overall average math score was 66.59. However, when comparing this number to the charter and public math scores by grade, only charter students in 9th and 11th grade scored higher than this average. There could be several reasons for this, and further analysis of the data - particularly comparing the number of schools and the total number of students separated by school type and grade - could lead to a deeper understanding of why the scores are separated in this way. In a similar vein, the current level of analysis clearly shows that charter schools have an average budget of around $872,626, while public schools' budgets average around $911,196, but further drilling down into the dataset would show how many schools belong to each category, as well as the average number of students per school. This deeper analysis would properly show the distribution of budgets across the schools within the district.

However, there were a few problems with the data itself, most notably in the large number of null values in `reading_score` and `math_score`, with a total of 1,968 and 982 null values for each variable, respectively. Because the total number of students with collected data is 19,514, the percentage of missing scores for `reading_score` and `math_score` are roughly 10% and 5%, respectively. With such a large percentage of missing values, the dataset is inevitably skewed, and it may be better to reconsider how the data was collected. If the missing values are because those students did not take the exams, it should clearly state that the goal is to compare students who have taken both the math and reading tests, in which case the affected rows should be removed. However, if the values are missing for other reasons, and the goal remains to compare all students within the district, a better route may be to change the way the data is collected.
