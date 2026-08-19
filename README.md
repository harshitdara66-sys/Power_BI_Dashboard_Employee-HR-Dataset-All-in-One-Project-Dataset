# 👥 HR Data Analytics Dashboard | Power BI Business Intelligence Project

<p align="center">

![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Advanced-blue?style=for-the-badge)
![Power Query](https://img.shields.io/badge/Power%20Query-ETL-success?style=for-the-badge)
![Data Modeling](https://img.shields.io/badge/Data%20Model-Star%20Schema-orange?style=for-the-badge)
![HR Analytics](https://img.shields.io/badge/HR-Analytics-purple?style=for-the-badge)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen?style=for-the-badge)

</p>

---

# 📌 Project Overview

This project is an **interactive HR Business Intelligence Dashboard** developed in **Microsoft Power BI**.

The dashboard transforms employee, training, performance, engagement, and recruitment data into meaningful workforce insights. It provides management with a centralized view of **headcount, attrition, compensation, employee performance, training investment, workforce diversity, and hiring trends**.

The project demonstrates an end-to-end Business Intelligence workflow including **ETL, Data Cleaning, Data Modeling, DAX, Time Intelligence, KPI Development, and Interactive Dashboard Design**.

---

# 🎯 Business Objectives

- Monitor overall workforce headcount
- Track active and terminated employees
- Analyze employee attrition
- Compare salary levels across departments
- Analyze employee tenure and career levels
- Measure employee performance
- Evaluate training participation and training costs
- Analyze workforce diversity
- Monitor hiring and recruitment trends
- Identify high-performing employees
- Support workforce planning and HR decision-making

---

# 📊 Dashboard Features

## Executive KPIs

- 👥 Total Headcount
- 🟢 Active Headcount
- 🔴 Terminated Employees
- 📉 Attrition Rate
- 💰 Average Salary
- 💵 Total Salary Cost
- ⏳ Average Tenure
- ⭐ Average Performance Rating
- 🎓 Training Cost
- 🏆 High Performer Percentage

---

## Workforce Analytics

- Department-wise Headcount
- Active vs Terminated Employees
- Career-Level Distribution
- Employee Tenure Analysis
- Workforce Composition
- Department Contribution to Total Headcount

---

## Compensation Analytics

- Average Salary
- Total Salary Cost
- Salary Band Analysis
- Department Average Salary
- Salary Ranking by Department
- Above-Average Salary Analysis

---

## Performance Analytics

- Average Performance Rating
- High Performer Count
- High Performer Percentage
- Department Performance Comparison
- Performance Classification
- Employee Performance Insights

---

## Training Analytics

- Total Training Cost
- Average Training Cost
- Training Cost by Department
- Training Cost Ranking
- Training Investment Analysis

---

## Attrition Analytics

- Overall Attrition Rate
- Department Attrition Analysis
- Termination Trends
- YTD Attrition
- Attrition Comparison
- Historical Workforce Movement

---

## Recruitment Analytics

- Recruitment Pipeline
- Applicant Status Analysis
- Application Stage Distribution
- Recruitment Performance
- Hiring Activity Analysis

---

## Workforce Diversity

- Gender Distribution
- Gender Diversity Ratio
- Department Diversity
- Workforce Composition

---

# 📈 Business Insights

The dashboard helps HR teams and business leaders:

- Identify departments with high employee concentration
- Monitor workforce growth and reduction
- Identify areas with higher employee attrition
- Compare compensation across departments
- Detect employees or groups above average salary levels
- Identify high-performing workforce segments
- Evaluate investment in employee training
- Monitor workforce diversity
- Compare hiring performance over time
- Support data-driven workforce planning

---

# 🛠 Tech Stack

| Technology | Purpose |
|------------|---------|
| Microsoft Power BI | Dashboard Development |
| Power Query | Data Cleaning & ETL |
| DAX | KPIs & Business Measures |
| Data Modeling | Relationships & Semantic Model |
| Star Schema | Analytical Data Architecture |
| Excel / CSV | Source Data |
| Git / GitHub | Version Control |

---

# 🧮 DAX Measures

The project includes a centralized **`_Measures`** table for reusable business calculations.

### Core HR Measures

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

### Workforce & Attrition Measures

```DAX
Attrition_Rate_%
Gender_Diversity_Ratio
Headcount_%_of_Total
Senior_Headcount
High_Performers_Count
High_Performer_%
```

### Compensation Measures

```DAX
Dept_Avg_Salary_AEXCEPT
Above_Avg_Salary_Flag
Salary_Rank_Dept
Salary_Formatted
```

### Training Measures

```DAX
Avg_Training_Cost
Total_Training_Cost
Training_Cost_Rank
Bench_Utilisation_%
```

### Time Intelligence Measures

```DAX
YTD_New_Hires
New_Hires_SPLY
New_Hires_YoY_%
Hires_Prior_3M
Attrition_Rate_YTD
```

The project uses advanced DAX concepts including:

- `CALCULATE`
- `DIVIDE`
- `SUMX`
- `AVERAGEX`
- `VALUES`
- `FILTER`
- `TOTALYTD`
- `DATESYTD`
- `SAMEPERIODLASTYEAR`
- `DATEADD`
- `USERELATIONSHIP`
- Context Transition
- Filter Context

---

# 🧹 Data Preparation

Data preparation was performed using **Power Query**.

### Transformation Steps

- Validated source tables
- Corrected column data types
- Converted joining and termination dates to Date
- Converted salary fields to numeric format
- Converted employee ratings to Whole Number
- Trimmed and cleaned text fields
- Standardized categorical values
- Validated employee identifiers
- Checked missing values
- Prepared tables for relationships
- Created analytical columns
- Validated data before loading into the model

---

# 🧱 Calculated Columns

The project contains several calculated employee attributes.

### Tenure

`Tenure_Years`

Calculates employee service duration based on joining and termination dates. Active employees use the current date for tenure calculation.

### Career Level

`Career_Level_Band`

Groups employees into defined career-level categories.

### Salary Classification

`Salary_Band`

Groups employees into salary ranges for compensation analysis.

### Employee Status

`Is_Active`

Creates an active/inactive employee indicator based on employee status.

### Employee Name

`Full_Name`

Creates a reusable full-name field for employee-level reporting.

---

# 📊 Data Model

The project follows a structured analytical data model.

### Main Employee Table

- EmployeeMaster

### Related Tables

- Training
- Performance
- EngagementSurvey

### Standalone Business Table

- Recruitment

---

## 🔗 Relationships

The primary employee relationships are:

```text
EmployeeMaster[Employee ID]
            │
            ├──────────────► Training[Employee ID]
            │
            ├──────────────► EngagementSurvey[Employee ID]
            │
            └──────────────► Performance[Employee ID]
```

Relationship design:

- **One-to-Many** relationships where applicable
- **Single-direction** filtering
- EmployeeMaster acts as the primary employee dimension
- Recruitment remains independent where Employee ID is unavailable

---

# 📅 Time Intelligence

The project includes advanced time-based HR analysis.

Examples:

```text
YTD New Hires
Previous-Year New Hires
Hiring YoY %
Prior 3-Month Hires
YTD Attrition Rate
```

Time-intelligence calculations use:

- `DATESYTD`
- `TOTALYTD`
- `SAMEPERIODLASTYEAR`
- `DATEADD`
- `CALCULATE`
- `USERELATIONSHIP`

This allows management to compare workforce activity across different periods.

---

# 📸 Dashboard Preview

```text
assets/
│
├── HR Dashboard Overview.png
├── Workforce Analytics.png
├── Attrition Analytics.png
├── Compensation Analytics.png
├── Training Analytics.png
└── Performance Analytics.png
```

> Add your exported Power BI dashboard screenshots to the `assets` folder and update the image links below.

```markdown
![HR Dashboard Overview](assets/HR%20Dashboard%20Overview.png)

![Workforce Analytics](assets/Workforce%20Analytics.png)

![Attrition Analytics](assets/Attrition%20Analytics.png)
```

---

# 🚀 Power BI Skills Demonstrated

- Power Query ETL
- Data Cleaning
- Data Transformation
- Data Modeling
- Relationship Management
- Star Schema Concepts
- Advanced DAX
- Filter Context
- Context Transition
- Time Intelligence
- KPI Cards
- Interactive Slicers
- Drill Down
- Drill Through
- Conditional Formatting
- Dynamic Business Metrics
- Dashboard Design
- Data Validation
- Performance Optimization

---

# 📈 Key Performance Indicators

| KPI | Description |
|-----|-------------|
| Total Headcount | Total employees in the dataset |
| Active Headcount | Currently active employees |
| Terminated Count | Employees who have left |
| Attrition Rate | Employee exit rate |
| Average Salary | Average employee compensation |
| Total Salary Cost | Overall salary expenditure |
| Average Tenure | Average employee service duration |
| Average Performance | Average workforce performance rating |
| Training Cost | Investment in employee development |
| High Performer % | Percentage of high-performing employees |
| Department Count | Number of departments represented |

---

# 📊 Dashboard Workflow

```text
Raw HR Data
      │
      ▼
Power Query
      │
      ▼
Data Cleaning & Transformation
      │
      ▼
Data Model & Relationships
      │
      ▼
Calculated Columns
      │
      ▼
DAX Measures
      │
      ▼
KPI Layer
      │
      ▼
Interactive Power BI Dashboard
      │
      ▼
Business Insights
```

---

# 🧪 Data Validation

The report includes validation of:

- Employee count
- Active employee count
- Terminated employee count
- Department totals
- Salary calculations
- Training costs
- Performance ratings
- Attrition calculations
- Relationship integrity
- Date-based calculations
- YTD calculations
- Previous-year comparisons
- Blank and invalid values

---

# ⚡ Performance Optimization

The model follows Power BI performance best practices:

- Removed unnecessary columns
- Used appropriate data types
- Centralized reusable measures
- Avoided unnecessary calculated columns
- Maintained simple relationships
- Used single-direction filtering
- Reduced unnecessary model complexity
- Used dedicated DAX measures for dynamic calculations
- Applied controlled filter removal where required

---

# 📂 Repository Structure

```text
HR-Data-Analytics-PowerBI
│
├── PR.4 (HR Data Analytics).pbix
│
├── Data
│   ├── EmployeeMaster
│   ├── Training
│   ├── Performance
│   ├── EngagementSurvey
│   └── Recruitment
│
├── assets
│   ├── HR Dashboard Overview.png
│   ├── Workforce Analytics.png
│   ├── Attrition Analytics.png
│   ├── Compensation Analytics.png
│   └── Training Analytics.png
│
├── README.md
└── LICENSE
```

---

# 💼 Business Value

This dashboard enables HR stakeholders to:

- Monitor workforce health
- Identify attrition risks
- Analyze compensation structures
- Evaluate employee performance
- Measure training investment
- Monitor workforce diversity
- Track hiring activity
- Improve workforce planning
- Support management decisions with data

---

# 🔥 Project Highlights

- Enterprise-style HR Analytics Dashboard
- Interactive Power BI reporting
- Advanced DAX calculations
- Dedicated measure table
- Time-intelligence analysis
- Employee-level analytical attributes
- Workforce KPI reporting
- Attrition analysis
- Salary analytics
- Training cost analytics
- Performance analytics
- Recruitment analysis
- Data validation
- Performance-focused data modeling

---

# 📚 Learning Outcomes

Through this project, I gained practical experience in:

- Business Intelligence
- HR Analytics
- Power BI Development
- Power Query
- M Language
- Data Modeling
- DAX
- Time Intelligence
- KPI Development
- Dashboard Design
- Data Visualization
- Data Validation
- Performance Optimization
- Analytical Thinking
- Business Problem Solving

---

# 🚀 How to Run the Project

### Requirements

- Microsoft Power BI Desktop
- Access to the project source data

### Steps

1. Clone or download the repository.
2. Open `PR.4 (HR Data Analytics).pbix`.
3. Open **Transform Data**.
4. Verify the source file/folder paths.
5. Update the source path if the dataset has been moved.
6. Verify relationships in **Model View**.
7. Click **Refresh**.
8. Validate the KPI values.
9. Explore the interactive dashboard.

---

# 🔐 Data Privacy

HR datasets may contain sensitive employee information.

For public GitHub repositories:

- Do not publish confidential employee information.
- Do not expose personal identifiers.
- Do not upload private HR records.
- Use anonymized or synthetic data for public demonstrations.
- Do not commit credentials or private connection details.

---

# 🔮 Future Enhancements

Possible future improvements include:

- Row-Level Security (RLS)
- Power BI Service deployment
- Scheduled data refresh
- Incremental Refresh
- Attrition prediction
- Workforce forecasting
- Employee engagement scoring
- Salary equity analysis
- Recruitment funnel conversion analysis
- What-if headcount scenarios
- Automated HR alerts
- Power BI deployment pipelines
- Microsoft Fabric integration

---

# 🤝 Contributing

Contributions and suggestions are welcome.

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Commit your changes
5. Push the branch
6. Submit a Pull Request

---

# 👨‍💻 Author

**Harshit Dara**

**Aspiring Data Analyst | Power BI Developer | Business Intelligence Enthusiast**

📧 Email: harshitdara66@gmail.com

💼 LinkedIn: https://www.linkedin.com/in/harshit-dara-77165135b

🌐 GitHub: https://github.com/harshitdara66-sys

---

# 📄 License

This project is licensed under the **MIT License**.

---

<p align="center">

## ⭐ If you found this project useful, please consider giving it a Star!

**Data → Insights → Decisions 📊**

</p>
