# P10_Edtech_Analysis

**A. Project Overview**

- This project 

_Explore more insights in the full Power BI dashboard_

**B. Dataset Information**

**Source**

- Synthetic dataset created for educational and portfolio purposes.
- The data structure and variables are designed to mirror real-world scenario in Vietnam.

**Period**

x

**Assumption (For Relationship Model in Power BI)**
- ParentEngagement Table Assumption:
  + The dataset does not clarify whether feedback_score reflects trial-class feedback (before enrollment) or course feedback (after enrollment).
  + In this project, we assume that ParentEngagement is recorded at the student level, independent of specific enrollments or courses.
  + Therefore, ParentEngagement is linked directly to the Students table via student_id.

**C. Methodoly**

x

**II. Key Findings & Actionable Plans**

_**Key Findings**_

- x

_**Actionable Plans**_

- x

**III. Roadmap & Guidelines** 



**E. Appendix**

**I. Relationship Model with Power BI**

**1. Fact & Dimension Classification**

| Dimension Tables | Fact Tables      |
| ---------------- | ---------------- |
| Students         | Assessments      |
| Mentors          | Enrollments      |
| Courses          | Payments         |
|                  | ParentEngagement |

**2. Relationship Decisions**

| Relationship                | Keep/Remove | Notes                                                                                                                     | Cardinality |
| --------------------------- | ----------- | ------------------------------------------------------------------------------------------------------------------------- | ----------- |
| Students → Assessments      | Remove      | Assessments already connect through Enrollments. Direct link would create redundant paths.                                | –           |
| Students → Enrollments      | Keep        | One student can have many enrollments.                                                                                    | One to Many |
| Students → Payments         | Remove      | Payments should be connected via Enrollments. Direct link would cause ambiguity.                                          | –           |
| Students → ParentEngagement | Keep        | Engagement data (feedback, interactions) is captured at student level. One student can have multiple engagement records.  | One to Many |
| Mentors → Assessments       | Remove      | No common key between Mentors and Assessments. No logical relationship.                                                   | –           |
| Mentors → Enrollments       | Remove      | No direct link; connection should flow through Students.                                                                  | –           |
| Mentors → Payments          | Remove      | No relation; Payments link through Enrollments, not Mentors.                                                              | –           |
| Mentors → ParentEngagement  | Remove      | No shared key; unrelated entities.                                                                                        | –           |
| Mentors → Students          | Keep        | One mentor can guide multiple students. Clear parent–child relationship.                                                  | One to Many |
| Courses → Assessments       | Remove      | Assessments are linked via Enrollments. Direct link would be redundant.                                                   | –           |
| Courses → Enrollments       | Keep        | One course can have many enrollments.                                                                                     | One to Many |
| Courses → Payments          | Remove      | Payments are tied to Enrollments, not directly to Courses.                                                                | –           |
| Courses → ParentEngagement  | Remove      | No common key; Courses are not directly related to Parent Engagement.                                                     | –           |
| Enrollments → Assessments   | Keep        | One enrollment can generate multiple assessments.                                                                         | One to Many |
| Enrollments → Payments      | Keep        | One enrollment can generate multiple payments.                                                                            | One to Many |
| Assessments → Payments      | Remove      | No common key between Assessments and Payments. No logical relationship.                                                  | –           |
| Payments → ParentEngagement | Remove      | No business relationship even though both have `student_id`; joining would cause many-to-many ambiguity and double-count. | –           |

**3. Relationship Model (Star Schema)**

![Relationship Model](https://github.com/CallmeNavin/P10_Edtech_Analysis/blob/main/Version%201/Visualization/Relationship%20Model%20w%20PowerBI.png)

_**F. About Me**_

Hi, I'm Navin (Bao Vy) – an aspiring Data Analyst passionate about turning raw data into actionable business insights.
I’m eager to contribute to data-driven decision making and help organizations translate analytics into business impact.
For more details, please reach out at:

🌐 LinkedIn: https://www.linkedin.com/in/navin826/

📂 Portfolio: https://github.com/CallmeNavin/
