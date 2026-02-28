PROJECT OVERVIEW

I created this project to investigate whether gene expression profiles can be used to predict relapse in breast cancer patients. Using publicly available microarray data from the NCBI Gene Expression Omnibus (GEO), I built a machine learning model to classify patients into relapse vs. non-relapse groups based on tumor transcriptomic signatures.

The below was my workflow:

1 Parse and preprocess raw GEO expression data

2 Build a predictive classification model

3 Evaluate model performance using standard metrics

4 Identify top predictive genes

5 Interpret findings in the context of breast cancer biology




DATASET DESCRIPTION

Samples: 286 breast cancer patients

Platform: Affymetrix HG-U133A microarray

Features: ~22,000 probe sets (gene expression values)

Target variable: Relapse status (0 = no relapse, 1 = relapse)

Each sample contains gene expression intensities measured from primary tumor tissue.

Due to the high dimensionality (~22k genes) and relatively small sample size (286 patients), feature selection was performed to reduce noise and improve model stability.




MACHINE LEARNING MODEL

Model used:
Logistic Regression (L2 regularized)
Training pipeline:
80/20 train-test split
Stratified sampling to preserve class balance
Feature scaling



MODEL PERFORMANCE

Test set results:
Accuracy ≈ 0.79
ROC AUC ≈ 0.77
Confusion matrix analysis showed reasonable performance, though sensitivity for relapse cases was lower than for non-relapse cases, likely due to class imbalance.
Given the small sample size and high-dimensional biological data, this level of performance is considered biologically meaningful rather than random.



PCA VISUALIZATION

Principal Component Analysis (PCA) was used to visualize global gene expression structure.
The PCA plot showed partial separation between relapse and non-relapse groups, indicating that transcriptomic patterns contain predictive signal, though not perfectly separable — which aligns with the complexity of cancer biology.




FEATURE IMPORTANCE AND BIOLOGICAL INTERPRETATION

Top predictive genes (after mapping probes to gene symbols using GPL96 annotation):

TCN1

KRT8

FABP5

CXCL13

TYMS

SIAH2

COX6A1

UQCRB

PRKACB

CSTA

These genes were ranked based on absolute logistic regression coefficients.



LITERATURE SUPPORT

Several of these genes are well-documented in breast cancer biology:

KRT8 (Keratin 8)
Epithelial cytoskeletal protein
Associated with tumor progression and metastasis
Reference:
Moll et al., Histochemistry and Cell Biology, 2008

FABP5 (Fatty Acid Binding Protein 5)
Involved in lipid metabolism
Overexpression linked to aggressive breast tumors
Reference:
Liu et al., Cancer Research, 2008

CXCL13
Chemokine involved in immune microenvironment
Associated with prognosis and immune infiltration in breast cancer
Reference:
Gu-Trantien et al., Journal of Clinical Investigation, 2013

TYMS (Thymidylate Synthase)
Key enzyme in DNA synthesis
Marker of proliferation
Target of 5-fluorouracil chemotherapy
Reference:
Johnston et al., Clinical Cancer Research, 1997

SIAH2
Hypoxia-regulated E3 ubiquitin ligase
Implicated in tumor progression and stress response
Reference:
Chan et al., Cancer Cell, 2009

These associations suggest that the model identified biologically plausible relapse-associated genes rather than random noise.




CONCLUSION

This project demonstrates that gene expression profiles from primary tumors contain predictive information for breast cancer relapse.
Using classical machine learning methods and biologically grounded interpretation, the model achieved meaningful predictive performance and identified genes supported by published cancer literature.
