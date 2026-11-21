*Project Deliverable 1: Data Collection, Cleaning, and Exploratory Data Analysis*
*Group: GoodGrace*
*Student Names:* Anusha Sharma and Ranju Khnanal
*University:* University of the Cumberlands
*Course:* MSCS 634 – Advanced Big Data and Data Mining
*Instructor:* Satish Penmatsa
*Submission Date:* November 20, 2026



## Dataset and source

•⁠  ⁠*Name:* Breast Cancer Wisconsin (Diagnostic) (WDBC), available from the UCI Machine Learning Repository.
•⁠  ⁠*UCI original:* https://archive.ics.uci.edu/dataset/17/breast+cancer+wisconsin+diagnostic
•⁠  ⁠*Reproducible access:* scikit-learn ⁠ sklearn.datasets.load_breast_cancer(as_frame=True) ⁠; this copy runs without downloading a file.
•⁠  ⁠*Original dataset:* 569 observations, 30 numerical input measurements, and one binary diagnosis label.
•⁠  ⁠*Selected concise dataset:* *569 records × 11 columns* — *10 mean nuclear measurements* (radius, texture, perimeter, area, smoothness, compactness, concavity, concave points, symmetry, fractal dimension), plus ⁠ diagnosis ⁠ (⁠ benign ⁠ or ⁠ malignant ⁠).
•⁠  ⁠*Purpose:* Learn a full, defensible data-mining preparation process in a small, auditable real-world dataset. The diagnosis label is an existing retrospective label, not a clinical recommendation.

## Repository layout

⁠ text
MSCS_634_ProjectDeliverable_1/
├── README.md
├── requirements.txt
├── Deliverable_1_Data_Cleaning_EDA.ipynb
├── ranju - Assignment (Illustrated).docx
├── data/
│   └── wdbc_cleaned.csv
└── figures/
    ├── 01_diagnosis_distribution.png
    ├── 02_radius_and_area_histograms.png
    ├── 03_concave_points_by_diagnosis.png
    ├── 04_feature_correlation_heatmap.png
    ├── 05_radius_area_scatter.png
    ├── 06_analysis_workflow.png
    ├── 07_selected_feature_structure.png
    ├── 08_cleaning_audit_dashboard.png
    ├── 09_iqr_outlier_summary.png
    └── 10_classwise_feature_means.png
 ⁠

## How to run

1.⁠ ⁠Install Python 3.10+ and Jupyter Notebook or JupyterLab.
2.⁠ ⁠From the repository folder, install the dependencies with ⁠ pip install -r requirements.txt ⁠.
3.⁠ ⁠Open ⁠ Deliverable_1_Data_Cleaning_EDA.ipynb ⁠ and select *Run All*.
4.⁠ ⁠The notebook loads the original UCI dataset through scikit-learn, applies the feature selection and checks, and saves its audited CSV and figures in ⁠ data/ ⁠ and ⁠ figures/ ⁠ automatically.
5.⁠ ⁠No external dataset download is necessary for the notebook.

## Data cleaning and quality checks

I inspected shape, column data types, missingness, infinities, exact duplicate records, invalid negative measurements, and basic feature distributions. The original selected extract has *zero missing values* and *zero exact duplicate rows*; therefore no imputation or deletion was needed. The pipeline includes conditional numeric coercion, validity checks, median imputation if missing data are encountered, and exact-duplicate removal if needed.

I screened extreme observations with the *1.5 × IQR rule, but deliberately retained flagged observations because an extreme tumor measurement is not automatically a corrupted value. Specifically, mean area had **25 IQR-flagged values* and mean radius had *14. All **569 records* were retained in the clean dataset.

## EDA: verified highlights

•⁠  ⁠*Class balance:* 357 benign (*62.7%) and 212 malignant (37.3%*).
•⁠  ⁠*Size by diagnosis:* mean radius of approximately *12.147* for benign records versus *17.463* for malignant records.
•⁠  ⁠*Area by diagnosis:* mean area of approximately *462.790* for benign records versus *978.376* for malignant records.
•⁠  ⁠*Shape difference:* mean concave points are approximately *0.026* for benign and *0.088* for malignant cases.
•⁠  ⁠*Multicollinearity:* correlation of ⁠ mean radius ⁠ and ⁠ mean perimeter ⁠ is about *0.998. ⁠ mean radius ⁠ and ⁠ mean area ⁠ correlate at about **0.987*.
•⁠  ⁠*Charts and diagrams:* Ten image files are provided, including an analysis workflow, predictor map, cleaning dashboard, IQR screening counts, diagnosis distribution, feature histograms, diagnosis-wise boxplot, correlation heatmap, radius-area scatterplot, and class-wise means. Each is generated in the notebook and discussed in the revised Word report.

## Challenges and resolutions

*No missing entries or duplicates:* I documented the result rather than artificially altering a clean benchmark. The notebook shows what would happen conditionally if such issues arose.

*Potential outliers:* Instead of deleting meaningful extremes, I retained them and documented IQR counts. Future training should evaluate robust scaling only where justified.

*Correlated variables:* Size-related measurements are highly related. I will compare feature selection or regularized alternatives in later modeling.

*Unequal label counts:* Future classification will use stratified splits and report minority-class recall, F1 and ROC-AUC, not accuracy alone. Fitted transformations must use training data only to prevent leakage.

## Next deliverables

For *regression, a defensible continuous outcome is ⁠ mean area ⁠ (removed from inputs when predicted); the correlation among size variables must be interpreted carefully. For **classification, ⁠ diagnosis ⁠ can be predicted using stratified validation. For **clustering* and *association rules*, standardized and appropriately binned numeric measures can reveal descriptive groups and co-occurrences.

## Interpretation and ethics

These data are retrospective, relatively small, and do not include demographic attributes needed to evaluate fairness across patient subgroups. The plotted associations are not causal results, and this educational dataset must not be used as a clinical diagnostic tool.

## Recent scholarly sources (APA 7)

Deepthi, Nayak, A., & Panicker, R. O. (2026). Independent evaluation of machine learning and deep learning models for breast cancer detection. PLOS Digital Health, 5(9), e0001747. https://doi.org/10.1371/journal.pdig.0001747

de Vargas, V. W., Aranda, J. A. S., Costa, R. D. S., Pereira, P. R. da S., & Barbosa, J. L. V. (2023). Imbalanced data preprocessing techniques for machine learning: A systematic mapping study. Knowledge and Information Systems, 65(1), 31–57. https://doi.org/10.1007/s10115-022-01772-8

Zhu, J., Zhao, Z., Yin, B., Wu, C., Yin, C., Chen, R., & Ding, Y. (2025). An integrated approach of feature selection and machine learning for early detection of breast cancer. Scientific Reports, 15, Article 13015. https://doi.org/10.1038/s41598-025-97685-x
