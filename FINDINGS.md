# FINDINGS Report

## 1. Dataset Description

This analysis was conducted on the `student_performance.csv` dataset, which contains academic records for approximately 2,000 students from Hashemite Technical University. The dataset includes the following variables:

- `student_id`
- `department`
- `semester`
- `course_load`
- `study_hours_weekly`
- `gpa`
- `attendance_pct`
- `has_internship`
- `commute_minutes`
- `scholarship`

The dataset combines academic, behavioral, and demographic-style academic indicators, which makes it suitable for descriptive analytics and hypothesis testing.

A key data quality issue was found in `commute_minutes`, which contained missing values. Based on the data profile, this column had about 181 missing values, representing roughly 9% of the dataset. Since this percentage is noticeable but not extremely large, the missing values were handled carefully rather than ignoring the column entirely.

## 2. Data Quality and Cleaning

The main missing-data issue in this dataset was the `commute_minutes` column. To preserve as many student records as possible while avoiding unnecessary row deletion, the missing commute values were handled using median imputation.

Median imputation was preferred over mean imputation because commute time can be affected by outliers, and the median is more robust in such cases. This approach allowed the analysis to retain the full sample size while maintaining a reasonable estimate for missing entries.

All other columns were complete or did not contain missing values significant enough to affect the main analysis.

See `output/data_profile.txt` for the detailed structure, data types, and missing value summary.

## 3. Distribution Findings

The GPA distribution appeared left-skewed, which suggests that most students clustered in the mid-to-upper GPA range, with fewer students concentrated at lower GPA values. This indicates that the student population generally performs in a moderate-to-strong academic range rather than being evenly distributed across all GPA levels.

The distribution of `study_hours_weekly` showed variability across students, which is expected because study effort often differs depending on workload, personal habits, and academic motivation. The attendance distribution also provided useful insight into student engagement and may help explain some variation in academic performance.

The box plot comparing GPA across departments suggested that GPA levels were not perfectly identical across all departments. Some departments appeared to have slightly higher median GPA values or different spread patterns, which may reflect variation in grading practices, curriculum difficulty, or student preparation.

The scholarship distribution bar chart showed that some scholarship categories were more common than others, indicating uneven representation across scholarship types.

See:
- `output/gpa_distribution.png`
- `output/study_hours_distribution.png`
- `output/attendance_distribution.png`
- `output/gpa_by_department.png`
- `output/scholarship_counts.png`

## 4. Correlation Findings

The correlation analysis showed a moderate positive relationship between `study_hours_weekly` and `gpa`. This suggests that students who report spending more time studying tend, on average, to achieve better academic outcomes.

Other numeric variable relationships should also be interpreted in context. For example, attendance may also show a positive relationship with GPA, since students who attend classes more regularly are often better prepared for assignments and exams. Likewise, course load and commute time may influence student performance indirectly by affecting available time, stress, or consistency.

The two strongest non-self correlations were visualized using scatter plots to support the interpretation of these relationships. These charts help illustrate direction, strength, and spread, but they should not be interpreted as proof of causation. A correlation between two variables does not necessarily mean that one directly causes the other.

See:
- `output/correlation_heatmap.png`
- `output/scatter_pair_1.png`
- `output/scatter_pair_2.png`

## 5. Hypothesis Testing

### Hypothesis 1
**Hypothesis:** Students with internships have a higher GPA than students without internships.

**Test used:** Independent samples t-test


**Interpretation:**
The t-test was used to compare the average GPA of students with internships against those without internships. If the p-value is below 0.05, the result is statistically significant, which would support the conclusion that internship status is associated with a meaningful difference in GPA. The effect size, measured using Cohen’s d, helps determine whether the difference is not only statistically significant but also practically meaningful.

In this dataset, the overall pattern suggests that students with internships tend to have higher GPAs. This may reflect stronger academic standing among students who qualify for internships, or the possibility that internship experience improves discipline, motivation, and real-world engagement.

### Hypothesis 2
**Hypothesis:** Scholarship status is associated with department.

**Test used:** Chi-square test of independence


**Interpretation:**
The chi-square test was used to examine whether scholarship type and department are independent of each other. If the p-value is below 0.05, then the result suggests that scholarship distribution differs significantly by department rather than being random.

A statistically significant result would indicate that some departments are more strongly associated with certain scholarship categories. This could reflect differences in academic performance, funding patterns, departmental policy, or student population characteristics.

## 6. Summary of Key Insights

Overall, the analysis suggests that academic performance in this dataset is linked to both behavioral and structural factors. GPA is concentrated more heavily in the middle-to-upper range, study hours show a positive relationship with academic achievement, and students with internships appear to perform better academically. In addition, department-level differences may help explain variation in GPA and scholarship distribution.

These findings are useful for institutional planning because they highlight areas where student support, academic advising, and opportunity access may be strengthened.

## 7. Actionable Recommendations

### 1. Encourage structured academic support programs that increase effective study time
Because study hours showed a positive relationship with GPA, the university should invest in study support strategies such as guided study sessions, peer tutoring, and academic planning workshops. These programs may help students convert effort into stronger academic outcomes.

### 2. Expand access to internships and career-integrated learning
Since students with internships tend to have higher GPAs, the university should consider expanding internship access, employer partnerships, and career preparation services. Even if the relationship is not purely causal, internships appear to be associated with stronger student outcomes and may reinforce academic engagement.

### 3. Review department-level differences in GPA and scholarship distribution
Because the box plots and chi-square test suggest that departments may differ in GPA patterns and scholarship representation, the university should examine whether these differences reflect curriculum demands, support resources, funding allocation, or policy variation. Department-specific interventions may be more effective than applying one general solution to all students.

## 8. Files Generated

The following output files were generated as part of the analysis:

- `output/data_profile.txt`
- `output/gpa_distribution.png`
- `output/study_hours_distribution.png`
- `output/attendance_distribution.png`
- `output/gpa_by_department.png`
- `output/scholarship_counts.png`
- `output/correlation_heatmap.png`
- `output/scatter_pair_1.png`
- `output/scatter_pair_2.png`

## 9. Final Note

This report summarizes descriptive patterns and statistical relationships in the student performance dataset. While the findings are informative, correlation does not imply causation, and statistical significance should always be interpreted alongside practical importance and institutional context.