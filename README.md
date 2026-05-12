
**University of Petra, Graduation Projects, Business Intelligence, 20252**

**AN INTERACTIVE MACHINE LEARNING FRAMEWORK FOR PREDICTING 
TYPE 2 DIABETES VIA LIFESTYLE INDICATORS**

**Raneem Rawwas — 202111039**

**Supervised by: Dr. Ayman Mansour**

**Course: 307498 – Graduation Project**

**Second Semester 2025/2026**

----------------------------------------------------------------------------------

## [Table of Content](docs.domcumentation.md#table-of-content) 

- ### [**Abstract**](docs/documentation.md#abstract)
- ### [**Acknowledgment**](docs/documentation.md#acknowledgment)
- ### [**Business Intelligence Project Description and Objectives**](docs/documentation.md#business-intelligence-project-description-and-objectives)
- ### [**Data Research and Acquiring Effort**](docs/documentation.md#data-research-and-acquiring-effort)
- ### [**Data Description and Understanding**](docs/documentation.md#data-description-and-understanding)
- ### [**Data Primary Cleaning and Transformation**](docs/documentation.md#data-primary-cleaning-and-transformation)
- ### [**Data Visualization and Insights**](docs/documentation.md#data-visualization-and-insights)
- ### [**Dashboard Design & Business Insights**](docs/documentation.md#dashboard-design--business-insights)
- ### [**Advanced Analytics and AI Modeling**](docs/documentation.md#advanced-analytics-and-ai-modeling)
- ### [**Tools Research and Selection Effort**](docs/documentation.md#tools-research-and-selection-effort)
- ### [**Project Deployment Effort – Use Case**](docs/documentation.md#project-deployment-effort-use-case)
- ### [**Results**](docs/documentation.md#results)
- ### [**References**](docs/documentation.md#references)
----------------------------------------------------------------------------------


**Abstract :**

Type 2 diabetes is one of the most prevalent chronic diseases worldwide, and early identification of at-risk individuals is critical for timely intervention and prevention. This project presents an interactive machine learning framework designed to predict the probability of Type 2 diabetes based on lifestyle and health indicators.
The project utilized two data sources: the CDC BRFSS 2015 dataset (70,692 records, 50/50 balanced split, 21 features), and real laboratory data provided by Smart Lab Laboratories under a formal data agreement. Dietary recommendation data was sourced from NutriPlus Nutritional Center under the supervision of Dr. Islam JadAlla.
Two models were developed. The first is a predictive model trained on the CDC dataset using Random Forest, XGBoost, CatBoost, ANN, and a Stacking Ensemble, with Bayesian hyperparameter optimization via Optuna. The second is a rule-based model derived from real laboratory data, used as the foundation for the user interface logic.
The project includes three interactive Tableau dashboards and a bilingual Arabic-English Streamlit interface featuring an intelligent prediction section and a diabetes awareness guide. A clear disclaimer is displayed stating the tool is for awareness purposes only and does not replace medical diagnosis. The model's outputs were reviewed and validated by Dr. Ahmad Jadallah from the University of Petra. A formal validation document is included in the documentation section of this repository.

----------------------------------------------------------------------------------
**Acknowledgments :**


First and foremost, I would like to express my sincere gratitude to my supervisor, Dr. Ayman Mansour, for his continuous guidance, valuable feedback, and support throughout every stage of this project.
I would also like to thank the faculty members of the Department of Business Intelligence and Data Analytics at the University of Petra for the knowledge and skills they provided throughout my academic journey.
Special thanks to Smart Lab Laboratories, under the management of Dr. Abdallah Alhariri, and a particular acknowledgment to Engineer Firas Alhussein for his cooperation in providing access to the laboratory data. I also extend my gratitude to Dr. Ahmad Jadallah from the University of Petra who reviewed and validated the model's outputs.
I am particularly grateful to Dr. Islam JadAlla and NutriPlus Nutritional Center for providing verified dietary recommendations, which formed the foundation of the user interface recommendations.
I am also grateful to the CDC for making the BRFSS dataset publicly available.
Finally, I would like to thank my family and friends for their patience, support, and encouragement throughout this journey.

----------------------------------------------------------------------------------
**Business Intelligence Project Description and Objectives**
What is this project about?

RiskSense is a bilingual interactive machine learning framework designed to predict the probability of Type 2 diabetes based on lifestyle and health indicators. The project was motivated by Jordan's position as one of the most affected countries in the MENA region, and by the silent nature of Type 2 diabetes — a disease that can progress for years without symptoms, making early detection critical. Many individuals remain undiagnosed until serious complications arise, and in some cases, the disease is only discovered after a life-threatening event.
What industry or business domain does it address?
Public health and healthcare analytics — specifically targeting early diabetes risk screening in Jordan and the broader MENA region.

How will it help the industry/business?

Explores the relationship between diabetes and lifestyle factors, demographic patterns, and health complications through three interactive Tableau dashboards
Gives individuals free access to a personalized risk assessment tool without requiring clinical visits or laboratory tests
Results include a risk probability alongside medically verified dietary recommendations tailored specifically to the Jordanian community
Supports the medical sector by increasing public awareness about diabetes risk, which can reduce the long-term burden on healthcare systems
Carries multi-level economic impact — from reducing individual healthcare costs through early prevention, to decreasing national expenditure on late-stage diabetes treatment and complications

What specific business problems are you solving?

Limited access to early diabetes screening in Jordan
Most individuals remain unaware of their risk until complications develop
Financial barriers ,most screening requires paid clinical visits

----------------------------------------------------------------------------------
**Data Research and Acquiring Effort**

What data did you search for and why?

Two types of data were needed for this project. The first is a large-scale labeled dataset linking lifestyle and health indicators to diabetes status — needed to train the predictive machine learning model. The second is real clinical laboratory data from Jordanian patients — needed to ground the project in local medical reality and build the rule-based logic behind the user interface recommendations.

How did you acquire it?

1.CDC BRFSS Dataset — downloaded directly from Kaggle as a public CSV file. No API or scraping was needed.The specific file used is diabetes_binary_5050split_health_indicators_BRFSS2015.csv , 70,692 records with a balanced 50/50 split between diabetic and non-diabetic cases across 21 lifestyle, behavioral, and demographic features.

📄 [View dataset on Kaggle](https://www.kaggle.com/datasets/alexteboul/diabetes-health-indicators-dataset/data?select=diabetes_binary_5050split_health_indicators_BRFSS2015.csv)

2. Smart Lab Laboratory Data
Real clinical laboratory results from Jordanian patients collected during 2025, covering 11 lab tests including HbA1c (used as the diabetes target variable), CRP, Triglycerides, GGT, Creatinine, and others. Provided under a formal NDA — documentation available in the repository.

📄 [View NDA](smart_lab_NDA.jpg)

----------------------------------------------------------------------------------
**Data Description and Understanding**
CDC BRFSS 2015 Dataset
The dataset used is the diabetes_binary_5050split_health_indicators_BRFSS2015.csv file, publicly available on Kaggle. It contains 70,692 records with a perfectly balanced 50/50 split between diabetic and non-diabetic cases across 21 features covering lifestyle behaviors, chronic conditions, and demographic information. The dataset contains no missing values.

Data Dictionary
| Variable Name | Role | Type | Description | Missing Values |
|---|---|---|---|---|
| ID | ID | Integer | Patient ID | No |
| Diabetes_binary | Target | Binary | 0 = no diabetes, 1 = prediabetes or diabetes | No |
| HighBP | Feature | Binary | 0 = no high BP, 1 = high BP | No |
| HighChol | Feature | Binary | 0 = no high cholesterol, 1 = high cholesterol | No |
| CholCheck | Feature | Binary | 0 = no cholesterol check in 5 years, 1 = yes | No |
| BMI | Feature | Integer | Body Mass Index | No |
| Smoker | Feature | Binary | Smoked at least 100 cigarettes in lifetime. 0 = no, 1 = yes | No |
| Stroke | Feature | Binary | Ever told you had a stroke. 0 = no, 1 = yes | No |
| HeartDiseaseorAttack | Feature | Binary | Coronary heart disease or myocardial infarction. 0 = no, 1 = yes | No |
| PhysActivity | Feature | Binary | Physical activity in past 30 days. 0 = no, 1 = yes | No |
| Fruits | Feature | Binary | Consume fruit 1 or more times per day. 0 = no, 1 = yes | No |
| Veggies | Feature | Binary | Consume vegetables 1 or more times per day. 0 = no, 1 = yes | No |
| HvyAlcoholConsump | Feature | Binary | Heavy drinker (men >14/week, women >7/week). 0 = no, 1 = yes | No |
| AnyHealthcare | Feature | Binary | Has any health care coverage. 0 = no, 1 = yes | No |
| NoDocbcCost | Feature | Binary | Needed a doctor but couldn't afford it. 0 = no, 1 = yes | No |
| GenHlth | Feature | Integer | Self-rated general health. Scale 1–5 (1=excellent, 5=poor) | No |
| MentHlth | Feature | Integer | Days mental health was not good in past 30 days. Scale 0–30 | No |
| PhysHlth | Feature | Integer | Days physical health was not good in past 30 days. Scale 0–30 | No |
| DiffWalk | Feature | Binary | Serious difficulty walking or climbing stairs. 0 = no, 1 = yes | No |
| Sex | Feature | Binary | 0 = female, 1 = male | No |
| Age | Feature | Integer | 13-level age category. 1 = 18–24, 13 = 80+ | No |
| Education | Feature | Integer | Education level. Scale 1–6 (1=never attended, 6=college graduate) | No |
| Income | Feature | Integer | Income scale. Scale 1–8 (1=less than $10,000, 8=$75,000+) | No |

  ----------------------------------------------------------------------------------
**Tableau Dashboards**

Why choosing  Tableau

Tableau was selected as the visualization tool for this project due to its powerful ability to handle large datasets and create interactive, visually rich dashboards without requiring programming knowledge. Its drag-and-drop interface allows for rapid exploration of data patterns, and its support for calculated fields and data transformation made it possible to enhance and relabel the dataset directly within the tool. Tableau is widely used in business intelligence environments, making it a relevant and industry-standard choice for this type of analytical work.

Design Choices

A unified dark purple theme was applied across all three dashboards to maintain visual consistency throughout the project. A two-color system was used across all charts to represent binary values: purple was used to represent the positive case or the value 1, and teal was used to represent the negative case or the value 0. This means that for the diabetes variable, purple represents diabetic cases and teal represents non-diabetic cases, and the same logic applies consistently to all other binary features across the dashboards — for example, purple represents smokers, those with high blood pressure, or those with heart disease, while teal represents the opposite. This consistent color mapping makes it intuitive for the viewer to interpret any chart in the dashboard without needing additional explanation. The same design language was also carried into the machine learning interface, creating a cohesive visual identity for the entire project.

 Dataset & Feature Preparation
 
The dataset used for the dashboards is the CDC BRFSS 2015 balanced dataset, specifically the diabetes_binary_5050split_health_indicators_BRFSS2015.csv file, which contains 70,692 records with a 50-50 split between diabetic and non-diabetic cases across 21 features.
Before building the dashboards, several modifications were made to improve readability and make the visualizations meaningful to a general audience. All binary features that were originally stored as 0 and 1 were replaced with descriptive text labels. The following features were manually relabeled:

•	Diabetes Binary: 0 → Non-Diabetic, 1 → Diabetes

•	High BP: 0 → Normal BP, 1 → High BP

•	High Chol: 0 → Normal Cholesterol, 1 → High Cholesterol

•	Stroke: 0 → No Stroke, 1 → Had Stroke

•	Phys Activity: 0 → Not Active, 1 → Active

•	Chol Check: 0 → Not Checked, 1 → Checked

•	Fruits: 0 → No Fruits, 1 → Fruits

•	Veggies: 0 → No Veggies, 1 → Veggies

•	Diff Walk: 0 → Easy Walk, 1 → Diff Walk

•	Any Healthcare: 0 → No Healthcare, 1 → Got Healthcare

•	No Docbc Cost: 0 → Could Afford Care, 1 → Could Not Afford Care

•	Sex: 0 → Female, 1 → Male

•	Gen Hlth: 1 → Excellent, 2 → Very Good, 3 → Good, 4 → Fair, 5 → Poor

In addition, the following calculated fields were created to further enhance the data:

•  BMI BINS: Grouped raw BMI values into WHO standard categories — Underweight, Normal Weight, Overweight/Pre-Obese, Class I Obesity, Class II Obesity, and Class III Obesity. 

•  Education Labels: Converted education levels from numeric codes to descriptive labels — Never Attended School, Grades 1-8 (Elementary), Grades 9-11 (Some High School), Grade 12, Some College, and College Graduate. 

•  Heart Disease Label: Converted HeartDiseaseorAttack from 0/1 to No Heart Disease / Heart Disease. 

•  High Chol Label: Converted High Chol from 0/1 to Normal Cholesterol / High Cholesterol. 

•  Hvy Alcohol Cons Label: Converted heavy alcohol consumption from 0/1 to Non-Heavy Drinker / Heavy Drinker. 

•  Income Label: Converted income from numeric codes to dollar range labels — Less than $10K, $10K-$15K, $15K-$20K, $20K-$25K, $25K-$35K, $35K-$50K, $50K-$75K, and More than $75K. 

•  Phys Activity Label: Converted physical activity from 0/1 to Not Active / Active. 

•  Smoker Label: Converted smoker status from 0/1 to Non-Smoker / Smoker. 

•  Stroke Label: Converted stroke from 0/1 to No Stroke / Had Stroke. 

•  Age Label: Converted age codes 1-13 to actual age ranges — 18-24, 25-29, 30-34, 35-39, 40-44, 45-49, 50-54, 55-59, 60-64, 65-69, 70-74, 75-79, and 80+. 

•  Phys Hlth Label: Grouped days of poor physical health into four categories — No Poor Health Days, 1-10 Days, 11-20 Days, and 21-30 Days. 

•  Ment Hlth Label: Grouped days of poor mental health into four categories — No Poor Mental Health Days, 1-10 Days, 11-20 Days, and 21-30 Days. 

•  GenHlth Label: Converted general health numeric scores to Excellent, Very Good, Good, Fair, and Poor. 

•  Diabetes Rate: A calculated measure showing the rate of diabetes across different segments. 

•  Diabetic Cases: A calculated measure counting the total number of diabetic records. 

•  Number of Records: A calculated measure counting total records per segment.

--After all transformations and calculated fields were applied, the dataset used in Tableau currently contains 38 fields and 70,692 rows.


 Dashboard Classification Logic
 
The 21 features were distributed across three dashboards based on the nature and theme of each feature group. Lifestyle and behavioral features that reflect daily habits and modifiable physical indicators were grouped in the first dashboard. Social, demographic, and economic features that reflect the broader life context of individuals were grouped in the second dashboard. Features related to existing health conditions, overall health status, and physical or mental wellbeing were grouped in the third dashboard. This classification ensures that each dashboard tells a coherent and focused story.

All three dashboards were set to a fixed size of 1600 × 750 pixels to ensure a consistent and unified viewing experience across all views.

 Business Value of the Dashboards
From a business and public health perspective, these dashboards provide decision-makers, healthcare providers, and researchers with a clear visual understanding of how diabetes relates to lifestyle choices, socioeconomic conditions, and existing health complications. They can help identify high-risk population segments, support the design of targeted prevention campaigns, and guide resource allocation in healthcare systems. The interactive nature of the dashboards allows users to filter and explore the data dynamically, making them a practical tool for ongoing analysis.

Dashboard 1 — Lifestyle Factors
 [View Dashboard 1 — Lifestyle Factors](images/dashboard1.png)

This dashboard focuses on behavioral and lifestyle-related features that are directly linked to an individual's daily habits and modifiable physical characteristics. Features included: BMI, Physical Activity, Smoker, Fruits & Vegetables consumption, High Blood Pressure, High Cholesterol, and Heavy Alcohol Consumption.

•	BMI Distribution: Diabetic cases are most concentrated in the Overweight and Class I Obesity categories, confirming the strong link between excess weight and diabetes risk. Non-diabetic individuals are more spread across normal and lower BMI ranges.

•	Physical Activity: Inactive individuals show significantly higher diabetes counts (13,059) compared to inactive non-diabetic individuals (7,934), while active individuals show the opposite pattern, highlighting physical inactivity as a key risk factor.

•	Smoker: Smokers have a higher diabetic count (18,317) compared to non-smokers with diabetes (17,029), suggesting a moderate association between smoking and diabetes.
•	Healthy Diet (Fruits & Veggies): Individuals who consume neither fruits nor vegetables show higher diabetes counts. Those consuming both show better outcomes, though diet alone does not determine diabetes status.
•	High BP: Blood pressure cases rise steadily with age for diabetic individuals, peaking between ages 60-69, while non-diabetic individuals show a flatter trend across age groups.

•	High Cholesterol: High cholesterol is more prevalent among diabetic individuals, with a notably larger proportion of diabetic cases in the high cholesterol category compared to normal cholesterol.

•	Diabetes Cases: Confirms the balanced 50-50 split of the dataset with 35,346 records in each class.

•	Smoker Rate: Provides a quick visual of smoker vs non-smoker distribution across both diabetic and non-diabetic groups.

•	Alcohol for Heavy Drinkers: Shows that heavy alcohol consumption is more common among non-diabetic individuals (2,188) compared to diabetic ones (832), which may reflect survivorship or behavioral differences.


Dashboard 2 — Social & Demographic Patterns
 [View Dashboard  — Social & Demographic Patterns](images/dashboard2.png)

This dashboard focuses on socioeconomic and demographic features that reflect the broader social context in which individuals live. Features included: Age, Gender, Education, Healthcare Access, Income, and whether the individual avoided a doctor due to cost.

•	Age & Gender: Diabetes cases increase consistently with age for both males and females, peaking in the 60-69 age group. Both genders follow a similar trend, with diabetic cases (purple) growing more steeply than non-diabetic cases (teal) in older age groups.

•	Education: An inverse relationship exists between education level and diabetes prevalence. Individuals with lower education levels show higher diabetic proportions, while college graduates show a more balanced distribution, suggesting education is associated with better health awareness.

•	Healthcare Access: The majority of respondents across both groups have healthcare coverage. However, a small but notable proportion of diabetic individuals lack access, which may contribute to delayed diagnosis.
•	Income vs Diabetes: Diabetic cases consistently outnumber non-diabetic cases at every income level below $75K. At the highest income bracket (above $75K), non-diabetic individuals significantly outnumber diabetic ones (13,451 vs 7,195), clearly illustrating the role of economic status in diabetes risk.

•	Not Going to a Doctor Because of Cost: The majority of individuals in both groups could afford care, but those who could not afford care show a disproportionately higher count of diabetic cases, reinforcing the impact of financial barriers on health outcomes.

Dashboard 3 — Health Complications & General Health
 [View Dashboard  — Health Complications & General Health](images/dashboard3.png)
 

This dashboard focuses on existing health conditions and overall physical and mental wellbeing. Features included: Physical Health, General Health, Heart Disease, Mental Health, Stroke, and Difficulty Walking.

•	Physical Health: Diabetic individuals are heavily concentrated in the 21-30 days of poor physical health category, while non-diabetic individuals are predominantly clustered at zero poor health days, clearly reflecting the physical burden of diabetes.
•	General Health (GenHlth): Diabetic individuals overwhelmingly report Fair or Poor general health, while non-diabetic individuals predominantly report Very Good or Good health, making self-reported general health one of the strongest visual indicators of diabetes status in the dataset.

•	Heart Disease: Heart disease is more prevalent among diabetic individuals, with a visibly larger proportion of the diabetic bar occupied by heart disease cases compared to the non-diabetic group.

•	Mental Health: Diabetic individuals report higher frequencies of poor mental health days, with elevated counts maintained across a wider range of days compared to non-diabetic individuals, reflecting the psychological burden of living with a chronic condition.

•	Stroke: While stroke is relatively rare in both groups, it occurs at a higher rate among diabetic individuals, consistent with known cardiovascular complications of diabetes.

•	Difficult Walk: Diabetic individuals report significantly greater difficulty walking compared to non-diabetic individuals, aligning with known complications such as peripheral neuropathy and reduced mobility.







## [**Data Description and Understanding**](docs/documentation.md#data-description-and-understanding)
- **Data Dictionary**: Describe every field you're using and why it matters
- **Exploratory Data Analysis (EDA)**:
  - Charts and graphs showing data distribution
  - Patterns discovered
  - Correlations and relationships found
  - Insights relevant to your project objectives

  ----------------------------------------------------------------------------------


## [**Data Primary Cleaning and Transformation**](docs/documentation.md#data-primary-cleaning-and-transformation)
Describe all data preparation steps in sequence:
- Data type conversions
- Handling missing values
- Merging datasets
- Aggregation and appending
- Any other transformations applied
----------------------------------------------------------------------------------

## [**Data Visualization and Insights**](docs/documentation.md#data-visualization-and-insights)
- Include relevant charts and describe each one
- Explain the significance of each visualization
- Highlight key insights from your charts
- What patterns do these visualizations reveal?
----------------------------------------------------------------------------------

## [**Dashboard Design & Business Insights**](docs/documentation.md#dashboard-design--business-insights)
- Showcase your final BI Dashboard
- Organize by **Business Questions Answered**

For each chart/component:
```
Chart [#]: [Title]
Description: [What does this chart show?]
Insight Derived: [What does this tell the business? Why is this important?]
```

Examples:
- Chart 1: Sales Trend Analysis – Shows growth pattern

![An example of a chart.](images/image-rendered.webp)
> The chart shows a cat

- Chart 2: Customer Segmentation – Identifies high-value segments
- Chart 3: Regional Performance – Highlights top/bottom performers
----------------------------------------------------------------------------------

## [**Advanced Analytics and AI Modeling**](docs/documentation.md#advanced-analytics-and-ai-modeling)
- What type of model did you build? (Clustering, Predictive, Association, Generative AI, forecasting, agents, etc.)
- What pre built AI models did you use and how?
- What results were you seeking or what attribute are you predicting?
- **Model Characteristics**: Such as Accuracy, precision, recall, weights, parameters
- Include multiple iterations if applicable
- Explain your findings and model performance


----------------------------------------------------------------------------------


## [**Tools Research and Selection Effort**](docs/documentation.md#tools-research-and-selection-effort)
- What tools did you evaluate?
- Which tools did you ultimately choose?
- Why did you select these tools?
- How do they support your project?

Examples:
- Data Analysis: Python, R, SQL
- Visualization: Tableau, Power BI, Looker
- Deployment: Streamlit, Fast API, Gradio, Flask, Cloud platforms
----------------------------------------------------------------------------------

## [**Project Deployment Effort – Use Case**](docs/documentation.md#project-deployment-effort-use-case)
- How will a business user consume this project?
  - Interactive web dashboard (Streamlit)?
  - Scheduled reports?
  - Dashboard
  - Live API?
  - Mobile app?
- Implementation steps in chronological order
- If you built a prototype, describe deployment process
- Infrastructure and hosting considerations
----------------------------------------------------------------------------------

## [**Results**](docs/documentation.md#results)
- Summary of findings (2-3 paragraphs)
- Most important insights or charts in your opinion
- Evaluation and interpretation of results
- Business impact and recommendations
----------------------------------------------------------------------------------

## [**References**](docs/documentation.md#references)
List all sources cited in your project using a consistent citation format (APA, Chicago, etc.)


----------------------------------------------------------------------------------

## Code setup and dependencies Instructions
Write procedure for setup and running code.
for example:
1. Clone the repository: 
   ```bash
   git clone <repository-url>
   ```
2. Navigate to the project directory: 
   ```bash
   cd <project-directory>
   ```
3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
4. Run the application: 
   ```bash
   python app.py
   ```


----------------------------------------------------------------------------------




## Documentation Best Practices

✅ **Do's:**
- Write in clear, descriptive language documenting your work effort.
- Use consistent formatting and headings
- Include visuals (charts, screenshots, diagrams)
- Add links to your data sources and tools
- Update regularly as your project evolves
- Use version control (git commits with meaningful messages)

❌ **Don'ts:**
- Don't use Word documents – use Markdown (.md) for project documentation and version control
- Don't commit large data files directly – use `.gitignore` and reference external sources
- Don't leave sections incomplete – mark as TODO if not ready
- Don't forget to document your data sources and methodology

---
----------------------------------------------------------------------------------

## Flexibility by Project Type

**This template is flexible.** Adapt based on your project focus:

| Project Type | Emphasis | Key Sections |
|---|---|---|
| **Dashboard-Heavy** | Visualization & Design | Sections 8-9 (Dashboard, Visualizations) |
| **Predictive Analytics** | Advanced Modeling | Section 10 (AI/ML Modeling) |
| **Data Engineering** | Cleaning & Transformation | Section 7 (Data Prep) |
| **Business Analysis** | Insights & Recommendations | Sections 5-6, 13 (Data, Results) |
| **Web Application** | Deployment & Use Cases | Section 12 (Deployment) |

---

## Getting Started

1. **Fork this repository** to your GitHub account
2. **Clone your fork**: `git clone <your-fork-url>`
3. **Create your project directory structure** using the template above
4. **Start documenting in Markdown** – one `.md` file per major section
5. **Commit regularly**: `git add . && git commit -m "Add data analysis"` && `git push`
6. **Important --> Link everything in your main README.md** so it's easy to navigate

---

## Additional Template Files to Create

Your students should also create these supporting files:

### `.gitignore` - Prevent committing unnecessary files
```
# Data files (if large)
data/raw/*.csv
data/raw/*.xlsx
data/processed/*.parquet

# Python
__pycache__/
*.py[cod]
*$py.class
*.egg-info/
.venv/
venv/

# Notebooks
.ipynb_checkpoints/

# Models
models/*.pkl
models/*.joblib

# IDE
.vscode/
.idea/

# OS
.DS_Store
Thumbs.db
```

### `requirements.txt` - Python dependencies
```
pandas==2.0.0
numpy==1.24.0
matplotlib==3.7.0
seaborn==0.12.0
plotly==5.14.0
scikit-learn==1.3.0
jupyter==1.0.0
streamlit==1.25.0
sqlalchemy==2.0.0
```

### `docs/SETUP.md` - Environment setup guide
```
# Project Setup Guide

## Prerequisites
- Python 3.8+
- Git
- GitHub account

## Installation Steps
1. Clone your fork: `git clone <your-fork-url>`
2. Create virtual environment: `python -m venv venv`
3. Activate: `source venv/bin/activate` (Mac/Linux) or `venv\Scripts\activate` (Windows)
4. Install dependencies: `pip install -r requirements.txt`
5. Start Jupyter: `jupyter notebook`

## Data Setup
1. Download data from sources listed in docs/02_data_research.md
2. Place raw data in `data/raw/`
3. Run data cleaning scripts in `notebooks/`
```

### `docs/EVALUATION_CRITERIA.md` - Grading rubric
```
# Evaluation Criteria

| Criterion | Excellent (90-100%) | Good (80-89%) | Satisfactory (70-79%) | Needs Improvement (<70%) |
|---|---|---|---|---|
| **Project Definition** | Clear objectives, well-defined problem | Objectives stated, minor clarity issues | Objectives present but vague | Missing or unclear objectives |
| **Data Research** | Comprehensive sources, well-justified | Good sources, mostly justified | Limited sources, weak justification | Poor data selection |
| **Data Analysis** | Thorough EDA, insightful findings | Good analysis, clear insights | Basic analysis, some insights | Minimal analysis |
| **Visualizations** | Professional, insightful, well-labeled | Good quality, mostly clear | Acceptable but basic | Poor quality/unclear |
| **Dashboard Design** | Intuitive, answers key questions | Good design, mostly effective | Functional but cluttered | Poorly designed |
| **Advanced Analytics** | Sophisticated models, well-evaluated | Good models, clear methodology | Basic models, limited evaluation | Minimal or missing |
| **Documentation** | Clear, complete, well-organized | Good documentation, minor gaps | Adequate but some gaps | Incomplete/unclear |
| **Deployment** | Complete, production-ready | Good implementation plan | Basic implementation | No deployment plan |
| **Results & Insights** | Significant findings, business value | Good findings, clear implications | Adequate results, limited impact | Minimal results |
| **Code Quality** | Well-commented, organized, reproducible | Good structure, mostly reproducible | Adequate but messy | Difficult to understand |
```

---

## Need Help?

- **Markdown Guide**: [GitHub Markdown Documentation](https://guides.github.com/features/mastering-markdown/)
- **Git Tutorial**: [Git Basics](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository)
- **BI Tools**: Research and document your tool choices in Section 11
- **Data Sources**: APIs, UCI ML Repository, Government Open Data, Industry Datasets, Web scraping, etc.

---

**Good luck with your Business Intelligence graduation project!** 
