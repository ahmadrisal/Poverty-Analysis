# Dissertation on Poverty Analysis

Code for the empirical study on multidimensional poverty in Sulawesi Tengah (Indonesia), covering **factor analysis (FAMD)**, **clustering**, and **predictive modelling** at both **individual** and **household** levels.

> **Data not included.** This repository is **code-only**. See **Data Access** for instructions.

---

## Repository structure

```text
Dissertation on Poverty Analysis/
├─ Household Analysis/
│  ├─ 01_factor.Rmd
│  ├─ 02_cluster.Rmd
│  ├─ 03_model.Rmd
│  ├─ utils_household.R
│  └─ _targets.R
├─ Individual Analysis/
│  ├─ 01_factor.Rmd
│  ├─ 02_cluster.Rmd
│  ├─ 03_model.Rmd
│  ├─ utils_individual.R
│  └─ _targets.R
├─ Makefile
└─ README.md
```

---

## Software requirements

- **R 4.4.1** (or newer in the 4.4 series)  
- Recommended R packages (install on first use):  
  - **Data wrangling & viz:** `tidyverse`, `janitor`, `skimr`, `ggplot2`, `patchwork`  
  - **Factor analysis (FAMD):** `FactoMineR`, `factoextra`  
  - **Clustering:** `cluster` (Gower, PAM), `fpc`, `stats` (kmeans), `MASS` (MDS)  
  - **Modelling:** `caret`, `ranger` (Random Forest), `xgboost`, `pROC`, `ROCR`  
  - **Resampling/SMOTE:** `DMwR` (or `themis` if you prefer tidymodels)  
  - **Tables/knit:** `knitr`, `kableExtra`, `gt`  
  - **Pipeline:** `targets`, `tarchetypes`
 
---

## Data access

This project uses **SUSENAS** microdata (National Socio-Economic Survey) administered by **Statistics Indonesia (BPS)**. The data are **restricted** and **not distributed** in this repository.

- To request access, please **contact Statistics Indonesia (BPS)** through official channels.  
- After approval, place files in a **local, private** directory (not tracked by Git). The notebooks expect paths you will define at the top of each `.Rmd`.

---

## Reproduction notes

- **No central config file** is used. Paths, seeds, and scenario toggles are defined at the top of each notebook.  
- The **household-level Random Forest** (all variables) is the recommended model for deployment, balancing **accuracy**, **robustness**, and **interpretability**.  
- Exceptionally high metrics in the **individual/all-variables** scenario may be influenced by repeated household attributes at the individual level (inflated signals).  

---

## Conceptual summary (what this code implements)

- **Factor analysis (FAMD)** distils multidimensional socio-economic structure into interpretable factors:  
  - *Individual*: human capital/behaviour, household economic status, activity status, digital engagement.  
  - *Household*: socioeconomic capital, demography/dependency, labour/lifestyle.  

- **Clustering** reveals coherent poverty segments:  
  - Vulnerable large households (highest poverty) vs. young educated professional households (lowest).  
  - Factor-based clustering is more interpretable than full-variable clustering.  

- **Predictive modelling**:  
  - Full-variable inputs achieve the strongest raw metrics.  
  - **Household-level Random Forest** offers the most **reliable, policy-relevant** predictions.  
  - **Variable importance** highlights dependency burden, education, assets/housing quality, and financial/digital inclusion as key drivers.  

