
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

📄 [View NDA](../docs/smart_lab_NDA.pdf)
----------------------------------------------------------------------------------

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
