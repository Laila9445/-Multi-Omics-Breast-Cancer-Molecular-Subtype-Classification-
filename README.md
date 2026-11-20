# -Multi-Omics Breast Cancer Subtype Classification
This project successfully developed and refined a multi-omics pipeline for breast cancer subtype classification, integrating RNA-sequencing (RNA-seq) gene expression and DNA methylation data. The comprehensive analysis, from rigorous preprocessing to advanced machine learning and interpretability, provided valuable insights into the molecular underpinnings of breast cancer subtypes.

Key Achievements and Findings:
Robust Data Preprocessing and Integration:

RNA-seq data underwent DESeq2 VST normalization and careful sample alignment.
DNA methylation data was thoroughly cleaned, including filtering of probes with excessive missing values and imputation of remaining missing data. Only primary tumor samples were retained.
A novel strategy was implemented to maximize usable sample size by including samples with either RNA-seq or methylation data (or both), provided PAM50 subtype information was available. Missing omics data was imputed using feature-wise means.
A final integrated multi-omics dataset was constructed, combining 1,000 top variable RNA-seq genes and 1,000 top variable CpG sites, resulting in a dataset of 325 samples and 2,000 features.
Advanced Feature Selection and Dimensionality Reduction:

Lasso Regularization was effectively applied to the scaled multi-omics data, reducing the feature space from 2,000 to 136 highly discriminative features. This step is crucial for combating high dimensionality and focusing on truly impactful molecular markers.
Independent Component Analysis (ICA) was then used on these Lasso-selected features to further reduce dimensionality to 10 independent components (ICs). ICA aims to uncover underlying latent factors, potentially representing distinct biological processes, which can be more informative for classification than simple principal components.
Optimized Machine Learning Models:

Hyperparameter tuning was performed for Random Forest and XGBoost classifiers using GridSearchCV with StratifiedKFold cross-validation on the ICA-transformed data.
The Optimized Random Forest model emerged as the best performer, achieving a mean F1-macro score of 0.763 and an accuracy of 0.763 in rigorous Leave-One-Out Cross-Validation (LOOCV).
The Optimized XGBoost and SVC models also demonstrated strong performance, with F1-macro scores of 0.748 and 0.738, respectively, affirming the robustness of the multi-omics approach.
The multi-omics models significantly outperformed baseline RNA-only models evaluated earlier in the pipeline, underscoring the value of integrating epigenetic information.
Enhanced Model Interpretability with SHAP Analysis:

SHAP (SHapley Additive exPlanations) analysis was performed on the best-performing Optimized Random Forest model.
The overall SHAP summary plot highlighted the global importance of each of the 10 ICA components in driving subtype predictions. This provided a clear hierarchy of which underlying biological signals (represented by ICs) were most influential.
Subtype-specific SHAP bar plots offered critical insights into the unique sets of ICA components that were most important for classifying each individual breast cancer subtype (Basal-like, HER2-enriched, Luminal A, Luminal B). This demonstrated that the model leveraged distinct multi-omics patterns for each subtype.
Comprehensive Visualizations:

PCA plots visually confirmed improved subtype separation in the multi-omics data compared to RNA-only or methylation-only data.
Cumulative variance plots provided insights into the intrinsic dimensionality, showing that a small number of components captured a significant portion of variance in each omics layer.
Confusion matrices for the optimized models provided a detailed view of per-class classification performance.
Comparative bar plots of LOOCV metrics clearly illustrated the superior performance of the multi-omics integrated models.
