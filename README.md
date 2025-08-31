# P10_Edtech Analysis

**VERSION 1 - ANALYSIS WITH POWER BI**

**A. Project Overview**

- This project analyzes the company’s performance across seven key areas: Assessments, Courses, Enrollments, Mentors, Parent Engagement, Payments, and Students.
- The goal is to identify core problems and uncover opportunities for improvement.

![Dashboard Visulization](https://github.com/CallmeNavin/P10_Edtech_Analysis/blob/main/Version%201/Visualization/Overview.png)
_Explore more insights in the full Power BI dashboard_

**B. Dataset Information**

**Source**

- Synthetic dataset created for educational and portfolio purposes.
- The data structure and variables are designed to mirror real-world scenario in Vietnam.

**Period**

- Synthetic dataset simulating academic year 2024–2025.

**Assumption (For Relationship Model in Power BI)**
- ParentEngagement Table Assumption:
  + The dataset does not clarify whether feedback_score reflects trial-class feedback (before enrollment) or course feedback (after enrollment).
  + In this project, we assume that ParentEngagement is recorded at the student level, independent of specific enrollments or courses.
  + Therefore, ParentEngagement is linked directly to the Students table via student_id.

**C. Methodoly**

Data Cleaning in Excel → Relationship Modeling in Power BI → Visualization → Insight & Action Plan

**D. Key Findings & Actionable Plans**

_**Key Overview Findings**_

- Avg Payment > Avg Course Price → students are often paying more than the listed course price (due to combo purchases, multiple enrollments, or additional fees). Regardless of the reason, this indicates customers are willing to pay higher → positive signal.
- Attendance Rate ~70% → not low but should be increased to at least 80% to ensure higher learning quality and assessment outcomes expected from a reputable EdTech center. Homework completion rate is also close to Attendance Rate, therefore both need to be raised together (≥80%).
- Assessment Score ~70% → the center must deliver more outstanding academic results in order to compete with schools and leverage in marketing.

**_Key Problems_**

- Status – around ~50% of students are dropped/no-show. Reasons include: course schedule mismatch, low parent engagement from the start, and lack of follow-up after enrollment.
- Parent Feedback – evenly distributed (1/3 Good, 1/3 Average, 1/3 Poor), showing no strong satisfaction pattern → too average, not competitive enough.
- Mentor Specialization imbalance – Physical Education only accounts for ~1/3. Some mentors are overloaded → quality decreases, students less motivated → completion rate drops.

→ High incomplete enrollment status + Average parent feedback + Mentor imbalance → Low attendance + Low homework completion → Assessment Score stuck around 70 (not outstanding).

_**Actionable Plans**_

- AVG Payment, AVG Course Price: Maintain the current healthy pricing strategy while improving transparency in cost explanation to strengthen parents’ trust and ensure stable enrollment inflow.
- Increase Attendance Rate, Homework Completion Rate to ≥80% to push Assessment Score up to at least 85: Handle 03 key problems:
  + Improve early-stage engagement: stronger interaction immediately after enrollment, involve parents from the start, and better screen students before enrollment (need test/interview to validate motivation).
  + Transform “Average” feedback into “Good”, creating a competitive edge and motivating parents to push their children to attend: Increase communication by regular studying reports, two-way feedback (parents contribute → center responds); encouraging parents to join “Parent Day” to directly see student progress.
  + Rebalance mentors, Recruit additional Physical Education mentors.

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
