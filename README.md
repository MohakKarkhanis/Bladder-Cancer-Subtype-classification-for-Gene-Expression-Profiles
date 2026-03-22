# Project-1
Cancer Subtype classification for Gene Expression Profiles 

The following repository contains the code, methodology and results for classifying bladder cancer into its subtypes.

The [Steps_Followed.docx](https://github.com/MohakKarkhanis/Project-1/blob/main/Steps_Followed.docx) file describes every step implemented to achieve the project's goal, so it is highly recommended to download it for comprehensive reference. As GitHub supports a maximum of 2GB with LFS, the raw and cleaned datasets are not published in this repository as they account for a size >2GB. However, their contents, dimensions and processing steps are fully described in the document.

**Goal**
To build, evaluate and deploy a machine learning model for classifying cancer subtypes from high-dimensional gene expression profiles with a strong emphasis on interpretability and user-friendly interaction.

**Tools**
Language: Python
Data Processing: Pandas, NumPy
Machine Learning: Scikit-learn, Random Forest, XG Boost
Dimensionality Reduction: PCA, UMAP
Visualization and Interpretability: Matplotlib, Seaborn, Plotly, SHAP
Deployment: Streamlit

**Methodology**
1. Data Acquisition: Publicly Available bladder cancer data [TCGA-BLCA cohort](https://portal.gdc.cancer.gov/analysis_page?app=Downloads) was harvested using the GDC Data Transfer Tool. **_Number of Cases: 853, 39380 files- 412 for TCGA-BLCA, Tissue/Organ of Origin: Anterior Wall of Bladder, Bladder neck, Bladder, Dome of Bladder, Lateral wall of bladder, overlapping lesion of bladder, posterior wall of bladder, Trigone of Bladder, Urachus, Ureteric Orifice.**
2. Data Processing and Mapping: Gene Expression Profiles _specifically the fpkm_uq_unstranded numeric values_ were extracted and mapped to their respective MDA clinical labels _Luminal, Basal and TP53-like_ using a custom mapping process. **Dimensions of the Raw file (Rows x Columns) 25841160 x 5 | Dimensions after Processing (Rows x Columns) 13891140 x 40**
3. Dimensionality Reduction: The high-dimensional dataset was converted into a wide format. PCA was applied to capture significant variance, followed by UMAP to preserve both local and global structure of the orignal datafor distinct clustering. Samples are used as rows and individual genes are columns showcasing their gene expression profiles. **Dimensions (Rows x Columns) 229 x 59427**
4. Model Training: A Random Forest classifier was trained on the scaled data, achieving an overall accuracy of approximately 87% (0.8696- to be exact). **Classification Report (Only Precision |Recall | f1-score): Basal (0.89 | 0.89 | 0.89), Luminal (0.90 | 0.95 | 0.92), TP53-like (0.75 | 0.67 | 0.71)**
5. Visualizing Gene Importance using SHAP: Shapley Additive Explanations (SHAP) were utilized to understand feature importance, identifying specific genes that had the highest impact on the model's predictions. **Top 5: RUNX1T1, ANXA6, GATA3, AL148206.1, GFPT2**
6. Web Deployment: The trained model and necessary cache resources were saved using Joblib and deployed as an interactive web dashboard using Streamlit.

**Note**
Any novel gene expression data when formatted correctly (Rows: Samples, Columns: Genes) can be processed through the Streamlit server for real-time classification.

**Steps to Run the App**
1. Ensure streamlit is installed _pip install streamlit_.
2. Navigate to [Streamlit Folder](Streamlit) containing [App.py](Streamlit/App.py) and the [Trained Models](Streamlit/trained_models)






The Code file is "Codes for 1.ipynb"
