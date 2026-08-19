# 📊 HR Data Analytics — Power BI

> **Enterprise-style HR Analytics & Workforce Intelligence Dashboard**  
> A Power BI project designed to transform employee, training, performance, engagement, and recruitment data into actionable workforce insights.

---

## 📌 Project Overview

**HR Data Analytics** is an end-to-end Power BI analytics project focused on understanding workforce composition, employee attrition, compensation, performance, training investment, engagement, and recruitment activity.

The project demonstrates a production-oriented BI workflow:

**Raw Data → Power Query → Data Model → DAX → KPI Layer → Interactive Dashboard → Business Insights**

The solution is designed with maintainability, data quality, reusable measures, and business-oriented reporting in mind.

---

## 🎯 Business Objectives

The dashboard is designed to help HR and management teams:

- Monitor total and active headcount.
- Analyze employee attrition and termination trends.
- Compare salary levels across departments and employee groups.
- Evaluate employee tenure and career-level distribution.
- Measure employee performance.
- Analyze training participation and training costs.
- Understand workforce diversity.
- Track recruitment pipeline activity.
- Identify high-performing employees and departments.
- Compare current workforce metrics with historical periods.
- Support data-driven workforce planning and HR decision-making.

---

## 🧩 Data Domains

The analytical solution works across multiple HR business domains:

| Domain | Purpose |
|---|---|
| Employee Master | Employee demographics, employment status, salary and joining/termination information |
| Training | Training participation, cost and training-related metrics |
| Performance | Employee performance ratings |
| Engagement Survey | Employee engagement-related information |
| Recruitment | Applicant pipeline and recruitment status |
| Date / Time | Time-based analysis and time-intelligence calculations |

> **Note:** Recruitment is treated separately where employee-level keys are unavailable.

---

## 🏗️ Data Architecture

The Power BI model follows a structured relational/analytical approach.

### Core Relationship Design

```text
                    ┌──────────────────┐
                    │  EmployeeMaster  │
                    │   Employee ID    │
                    └────────┬─────────┘
                             │
             ┌───────────────┼────────────────┐
             │               │                │
             ▼               ▼                ▼
      ┌────────────┐  ┌───────────────┐  ┌─────────────┐
      │  Training  │  │ Engagement    │  │ Performance │
      │ Employee ID│  │ Employee ID   │  │ Employee ID │
      └────────────┘  └───────────────┘  └─────────────┘

                    ┌──────────────────┐
                    │      Date        │
                    └────────┬─────────┘
                             │
                    Time Intelligence
                             │
                             ▼
                    HR Analytical Layer
```

### Relationship Strategy

- `EmployeeMaster[Employee ID]` → `Training[Employee ID]`
- `EmployeeMaster[Employee ID]` → `EngagementSurvey[Employee ID]`
- `EmployeeMaster[Employee ID]` → `Performance[Employee ID]`
- Relationships are designed as **1-to-Many** where applicable.
- Filter direction is primarily **Single** from the employee dimension toward related fact/detail tables.
- Recruitment is maintained as a standalone analytical table when an Employee ID relationship is not available.

---

## 🔄 ETL / Data Preparation

### Power Query Transformation Pipeline

The data preparation process includes:

1. Imported source HR datasets.
2. Validated table structures and column data types.
3. Converted employment dates to **Date** data type.
4. Converted salary to numeric/decimal format.
5. Converted employee ratings to numeric values.
6. Applied `Trim` and `Clean` transformations to text fields.
7. Standardized categorical values.
8. Checked missing and invalid values.
9. Created employee-level calculated attributes.
10. Prepared tables for relationship modeling.
11. Validated relationship keys.
12. Loaded transformed data into the Power BI semantic model.

### Data Quality Controls

The project considers:

- Missing values
- Duplicate employee identifiers
- Invalid dates
- Incorrect numeric data types
- Inconsistent text formatting
- Relationship/key integrity
- Outlier salary values
- Invalid employee status values

---

# 🧮 DAX & Semantic Model

The project contains a dedicated **`_Measures`** table for centralized KPI and analytical measures.

This approach keeps business logic separate from raw data columns and improves model maintainability.

## Core Measures

Examples include:

```DAX
Total_Headcount
Active_Headcount
Terminated_Count
Avg_Salary
Total_Salary_Cost
Avg_Tenure
Distinct_Departments
Avg_Performance_Rating
```

## Workforce Analytics

```DAX
Attrition_Rate_%
Gender_Diversity_Ratio
Headcount_%_of_Total
Senior_Headcount
High_Performers_Count
High_Performer_%
```

## Compensation Analytics

```DAX
Dept_Avg_Salary_AEXCEPT
Above_Avg_Salary_Flag
Salary_Rank_Dept
Salary_Formatted
```

## Training Analytics

```DAX
Avg_Training_Cost
Total_Training_Cost
Training_Cost_Rank
Bench_Utilisation_%
```

## Time Intelligence

```DAX
YTD_New_Hires
New_Hires_SPLY
New_Hires_YoY_%
Hires_Prior_3M
Attrition_Rate_YTD
```

The time-intelligence layer uses functions and concepts such as:

- `TOTALYTD`
- `DATESYTD`
- `SAMEPERIODLASTYEAR`
- `DATEADD`
- `CALCULATE`
- `DIVIDE`
- `USERELATIONSHIP`

---

# 📈 Key KPI Layer

The dashboard is designed around executive-level HR KPIs.

| KPI | Business Meaning |
|---|---|
| Total Headcount | Total employees represented in the model |
| Active Headcount | Currently active employees |
| Terminated Count | Employees who have exited |
| Attrition Rate | Employee exit rate relative to workforce |
| Average Salary | Average employee compensation |
| Total Salary Cost | Aggregate salary expenditure |
| Average Tenure | Average employee service duration |
| Average Performance Rating | Overall workforce performance |
| Training Cost | Investment in employee development |
| High Performer % | Share of employees meeting high-performance criteria |
| Headcount % of Total | Department/workgroup contribution to total workforce |

---

# 📊 Dashboard Capabilities

The Power BI report supports analysis across multiple dimensions.

### Workforce

- Headcount
- Active vs terminated employees
- Department distribution
- Career-level distribution
- Tenure analysis

### Compensation

- Average salary
- Department salary comparison
- Salary bands
- Salary ranking
- Above-average salary identification

### Performance

- Performance rating distribution
- High-performer analysis
- Department-level performance comparison

### Training

- Training participation
- Training cost
- Average training cost
- Department training analysis
- Training cost ranking

### Attrition

- Attrition rate
- Attrition trends
- Termination analysis
- YTD attrition
- Historical comparison

### Recruitment

- Applicant pipeline
- Application status
- Recruitment-stage analysis

---

# 🧱 Calculated Columns

The model includes employee-level analytical attributes such as:

### Tenure

`Tenure_Years`

Calculates employee service duration based on joining and termination dates, using the current date for active employees.

### Career Level

`Career_Level_Band`

Classifies employees into career-level groups based on defined business rules.

### Salary Band

`Salary_Band`

Groups employees into salary ranges for compensation analysis.

### Employee Status

`Is_Active`

Creates a standardized active/inactive indicator from employment status.

### Employee Name

`Full_Name`

Combines employee name fields into a reusable display attribute.

---

# 🧠 Analytical Design Principles

The project follows these BI principles:

### 1. Separate Measures from Raw Data

Business logic is centralized in the `_Measures` table instead of creating unnecessary duplicate calculations.

### 2. Prefer Measures for Aggregations

Dynamic metrics such as headcount, salary, attrition, and percentages are implemented as measures wherever possible.

### 3. Use Explicit Filter Context

DAX calculations are designed to respect report filters while providing controlled context removal where required.

### 4. Reusable Business Logic

Common HR calculations are implemented once and reused across multiple visuals.

### 5. Time Intelligence

Date-based analysis is handled through dedicated time-intelligence measures rather than manually hard-coded calculations.

---

# 🎨 Report Design

Recommended report design principles include:

- Executive KPI cards at the top.
- Consistent visual hierarchy.
- Department and employee segmentation.
- Interactive slicers.
- Drill-down where appropriate.
- Clear titles and labels.
- Minimal visual clutter.
- Consistent number formatting.
- Currency formatting for salary/cost metrics.
- Percentage formatting for ratio and rate measures.

---

# 🔍 Business Questions Answered

The solution enables stakeholders to answer questions such as:

1. How many employees are currently active?
2. What is the overall attrition rate?
3. Which departments have the highest headcount?
4. Which departments have the highest average salary?
5. Which employees/departments have above-average compensation?
6. What percentage of employees are high performers?
7. How much is being spent on employee training?
8. Which departments have the highest training cost?
9. How has hiring changed over time?
10. How does current hiring compare with the previous year?
11. What is the average employee tenure?
12. Which career levels represent the largest portion of the workforce?
13. How does employee performance vary across departments?
14. What is the organization's salary cost?
15. How is workforce diversity distributed?

---

# 🧪 Validation & Testing

Before publishing the report, validate:

- Total employee count against the source.
- Active employee count against employment status.
- Department totals.
- Salary totals and averages.
- Training cost totals.
- Performance rating averages.
- Attrition calculations.
- Date relationships.
- YTD and previous-year calculations.
- Filter behavior across visuals.
- Relationship cardinality.
- Blank/error values.

---

# ⚡ Performance Optimization

The model is designed with Power BI performance considerations in mind:

- Remove unnecessary columns.
- Remove unused rows.
- Prefer numeric keys where practical.
- Avoid unnecessary calculated columns.
- Use measures for dynamic aggregations.
- Keep relationships simple.
- Avoid unnecessary bidirectional relationships.
- Centralize reusable DAX.
- Reduce high-cardinality columns when they are not required.
- Use a dedicated Date table for time intelligence.

---

# 🗂️ Recommended Repository Structure

```text
HR-Data-Analytics/
│
├── README.md
│
├── PowerBI/
│   └── PR.4 (HR Data Analytics).pbix
│
├── Data/
│   └── Source datasets
│
├── Documentation/
│   ├── Data_Model.md
│   ├── DAX_Measures.md
│   └── Business_Requirements.md
│
├── Screenshots/
│   ├── Executive_Dashboard.png
│   ├── Workforce_Analysis.png
│   └── HR_KPI_Dashboard.png
│
└── .gitignore
```

> Avoid committing confidential, personal, or production HR data to a public repository.

---

# 🚀 How to Use

### Requirements

- Power BI Desktop
- Source HR dataset(s)
- Access to the required data location

### Steps

1. Clone/download the repository.
2. Open the `.pbix` file using Power BI Desktop.
3. If required, update the source file/folder path.
4. Open **Transform Data** and verify Power Query sources.
5. Verify relationships in **Model View**.
6. Select **Refresh**.
7. Validate KPI totals.
8. Explore the report using slicers and filters.

---

# 🔐 Data Privacy

HR analytics can contain sensitive employee information.

For public GitHub repositories:

- Do not upload personally identifiable information.
- Do not publish employee names unless explicitly permitted.
- Remove confidential salary information.
- Remove private HR records.
- Use synthetic/anonymized datasets for demonstrations.
- Keep production credentials outside the PBIX/repository.

---

# 📌 Assumptions

- Employee ID is treated as the primary employee-level identifier.
- EmployeeMaster acts as the primary employee dimension.
- Training, Performance, and EngagementSurvey contain employee-level records.
- Recruitment does not necessarily represent current employees.
- Attrition calculations depend on the defined employee status and termination-date logic.
- Salary metrics use the salary field available in the source dataset.
- Time-intelligence calculations depend on correct date relationships.

---

# 🔮 Future Enhancements

Potential production enhancements include:

- Row-Level Security (RLS)
- Incremental Refresh
- Power BI Service deployment
- Scheduled refresh
- HR alerting
- Automated anomaly detection
- Workforce forecasting
- Attrition prediction
- Salary equity analysis
- Employee engagement scoring
- Recruitment funnel conversion rates
- What-if salary and headcount scenarios
- Automated deployment pipelines
- Microsoft Fabric integration
- Power BI deployment pipelines

---

# 🛠️ Technology Stack

| Technology | Usage |
|---|---|
| **Power BI Desktop** | Data modeling and dashboard development |
| **Power Query / M** | ETL and data transformation |
| **DAX** | Measures and analytical calculations |
| **Excel / CSV** | Source data where applicable |
| **Git / GitHub** | Version control and project portfolio |

---

# 📚 Skills Demonstrated

This project demonstrates practical knowledge of:

- Business Intelligence
- Data Cleaning
- ETL
- Power Query
- M Language
- Data Modeling
- Relationships
- Star-schema concepts
- DAX
- Filter Context
- Context Transition
- Time Intelligence
- KPI Development
- HR Analytics
- Dashboard Design
- Data Validation
- Performance Optimization
- Git/GitHub Project Management

---

# 💼 Portfolio Value

This project demonstrates an end-to-end BI workflow suitable for:

- Data Analyst roles
- Business Intelligence Analyst roles
- Power BI Developer roles
- HR Analytics roles
- Junior BI Developer roles

It highlights the ability to move from **raw business data to an analytical semantic model and decision-support dashboard**.

---

# 👨‍💻 Project Information

**Project:** HR Data Analytics  
**Platform:** Microsoft Power BI  
**Category:** Business Intelligence / HR Analytics  
**File:** `PR.4 (HR Data Analytics).pbix`

---

## ⭐ Project Highlights

- End-to-end Power BI analytics solution
- Structured data model
- Dedicated DAX measure layer
- HR workforce KPIs
- Attrition analytics
- Compensation analytics
- Training analytics
- Performance analytics
- Recruitment analysis
- Time-intelligence calculations
- Data quality validation
- Business-focused dashboard design

---

## 📄 License

This project is intended for educational, portfolio, and demonstration purposes unless a separate license is provided.

---

## ⭐ Support

If this project is useful for learning Power BI or HR analytics, consider giving the repository a ⭐ on GitHub.

**Built with Microsoft Power BI | Data → Insights → Decisions**

