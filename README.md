#Final Project: Personality Traits and Drug Use Patterns in the UCI Drug Consumption Dataset
--- 

##Project Overview
--- 
This project examines associations between demographic characteristics, personality traits (Big Five, impulsivity, sensation seeking), and legal/illegal drug use using the UCI Machine Learning Repository’s “Drug Consumption (Quantified)” dataset.

Our goals were to:

Clean and recode the raw dataset into an analysis-ready format

Generate descriptive statistics (Table 1 & Table 2)

Build multivariable logistic regression models examining illegal drug use

Produce an interactive visualization dashboard using R Shiny

This README documents the entire data-wrangling and analysis pipeline so that any new user can fully reproduce the project.

##Data Sources
---
Raw Dataset

Drug Consumption (Quantified) — UCI Machine Learning Repository

Original format: .ARFF

Converted to .csv using Python (simple format conversion, no processing)

Working Data File

CLEANING DATA DRUG.xlsx
Contains:

Demographics

Personality trait scores

Drug use variables

Raw categorical encodings that required recoding

##Repository Structure
---
project/
│
├── data/
│   └── CLEANING DATA DRUG.xlsx
│
├── code/
│   ├── FinalProject.Rmd
│   ├── TABLES CODING.Rmd
│   └── RShiny.Rmd
│
├── output/
│   ├── cleaned_dataset.csv
│   ├── Table1.csv
│   ├── Table2.csv
│   └── Figures/
│
└── README.md

##Software & Packages
---
R Version

R version 4.x.x

Packages Used
tidyverse
dplyr
readxl
janitor
nnet
ggplot2
shiny
tableone
broom

Other Tools

Excel (preliminary cleaning)

Python (format conversion only)


##Data Wrangling Pipeline
---
This section follows the Berkeley “How to Write Good Documentation” structure and includes all steps required for full reproducibility.

###Excel Pre-Cleaning

Performed in CLEANING DATA DRUG.xlsx:

Standardized variable names for readability

Replaced numeric-coded demographics with meaningful labels

Gender, ethnicity, country

Education categorized into Low / Medium / High

Removed unused variables

Verified no duplicate participant entries

Checked for impossible values or malformed fields

This produced a consistent dataset that could be imported into R cleanly.

###Importing Data into R

Done in FinalProject.Rmd:

library(readxl)
library(dplyr)

raw <- read_excel("data/CLEANING DATA DRUG.xlsx")

###Cleaning Pipeline in R (tidyverse)
####Handling Missing Data

Identified missing values

Converted placeholders (e.g., empty cells, “NA”) into proper NA

Verified that no drug-use variable contained impossible values

####Recoding Variables

Personality trait scores converted into Low / Medium / High categories

Drug use variables dichotomized:

User vs Non-user

Created composite exposure variables:

Any legal drug use = caffeine OR nicotine OR alcohol OR chocolate

Any illegal drug use = cocaine OR ketamine OR heroin OR LSD

####Creating Final Analysis Dataset

Selected only required variables

Ensured factors were properly ordered

Exported to /output/cleaned_dataset.csv

###Table Creation
Table 1 — Demographic & Personality Profile by Gender

Generated using tableone in TABLES CODING.Rmd

Variables included:

Age group

Education

Ethnicity

Country

Big Five personality traits

Impulsivity

Sensation Seeking

Individual drug use variables

Table 2 — Any Legal/Illegal Drug Use by Age & Education

Cross-tabulations

Chi-square or Fisher’s exact tests when needed

###Regression Modeling

Performed in FinalProject.Rmd:

Logistic regression predicting any illegal drug use

Adjusted for:

Gender

Age group

Education

For each personality trait:

Reference group = Low

Output ORs + 95% CI extracted into Table 3

###Step 6 — Interactive Dashboard

In RShiny.Rmd:

Dashboard includes:

Ability to explore drug use by demographic group

Personality trait distributions

Prevalence of each drug

Filters for gender, age, education

Run with:

shiny::runApp("RShiny.Rmd")

##Reproducibility Guide (Run Order)

A new user can fully reproduce the pipeline by following:

Clone this repository

Place raw Excel file in data/

Open FinalProject.Rmd and knit it

Open TABLES CODING.Rmd to regenerate Tables 1 & 2

Open RShiny.Rmd and run the dashboard

The cleaned dataset and tables will appear in /output.

##Contributors

Tanya Budhiraja
Ceasar 
Kenechukwu 
Cameron Diehl
