# Final Project: Personality Traits and Drug Use Patterns in the UCI Drug Consumption Dataset


## Project Overview
This project examines associations between demographic characteristics, personality traits; (neuroticism, extraversion, openness to experience, agreeableness, and conscientiousness, impulsivity, sensation seeking), and legal/illegal drug use using the UCI ML Repository’s “Drug Consumption (Quantified)” dataset.

Our goals were to:

Clean the dataset, generate descriptive statistics (Table 1, Table 2 & Table 3), use multivariable logistic regression models to examine legal and illegal drug use, and produce an interactive visualization dashboard using R Shiny. 

This README documents the entire data-wrangling and analysis pipeline so that any new user can fully reproduce the project.

## Data Source
Dataset: Drug Consumption (Quantified) — UCI Machine Learning Repository
Original format: .data
Converted to .csv using Python 
Working Data File: CLEANING DATA DRUG.xlsx


### Data Cleaning Workflow (Overview)
Began with raw CSV import; no modifications applied at this stage.
Performed step-by-step cleaning across multiple Excel sheets to ensure transparency and reproducibility.
Final product: an analysis-ready dataset with standardized variables, recoded categories, and invalid cases removed.

1. RAW Data Import
Loaded CSV file using Excel’s import wizard.
Preserved original variable names and raw coding

2. Variable Renaming (DATA_RENAMED):
Applied metadata dictionary to create consistent, readable names.
Examples: nscore -> Neuroticism, amphet -> Amphetamine_Use.
Used copy-paste transpose to standardize labels across all columns.

3. Demographic Recoding (DATA_RECODED_DEMO):
Converted numeric codes into interpretable categories via lookup tables.
Recoded Age, Gender, Education, Country, and Ethnicity.
Example: –0.95197 -> Age 18–24, 0.48246 -> Female.

4. Personality Variable Categorization (DATA_RECODED_PERSONALITY)
Categorized personality scores (NEO-FFI-R, BIS-11, ImpSS) into Low / Medium / High.
Thresholds applied:
Low: < –1
Medium: –1 to +1
High: > +1
Original numeric variables retained for reference.

5. Drug Use Recoding (DATA_DRUGS_RECODED):
Recoded drug-use levels from CL0–CL6 into descriptive text.
Scheme included:
Never Used ->  Used Last Day
Completed using manual Find & Replace for consistency.

6. Removal of Invalid Responders (DATA_EXCLUDED_SEMERON)
Identified participants who reported using the fictitious drug Semeron.
Excluded any row not marked “Never Used.”
Approximately 8 invalid records were removed to protect data integrity.

7. Core Clean Dataset (DATA_CLEAN_FINAL)
Checked for missingness, outliers, type mismatches, and recoding errors.

8. Education Grouping (DATA_RECODED_EDUCATION)
Collapsed detailed education responses into: Low / Medium / High.
Definitions:
Low = left school ≤18
Medium = technical or university degree
High = postgraduate

9. Drug Use Binary Classification (DATA_RECODED_DRUGS_BINARY)
Simplified 19 drug-use variables into binary: User vs. Non-user.
Non-User = Never or >10 years ago.
User = any use within the past decade.

10. Final Analysis Dataset (DATA_FINAL_ANALYSIS)
Merged all cleaned and recoded variables into one dataset.
Ensured variables are standardized and analysis-ready

## Repository Structure
CLEANING DATA DRUG.xlsx — Dataset with standardized variable names and recoded demographic labels, used as the input for all analyses.

FinalProject.Rmd: This file loads the fully cleaned and standardized drug use dataset and performs a series of visual analyses to explore patterns in personality traits and substance use. It restructures the data into long formats, classifies drugs of interest as legal or illegal, and generates boxplots comparing personality scores between users and non-users across drug categories. The script also creates heatmaps to show how drug use varies across combined age and education groups—overall and separately for male and female participants and produces histograms illustrating drug-use patterns across gender, education level, and age groups.

RShiny.Rmd: This Shiny dashboard provides an interactive platform for exploring relationships between substance use, demographics, and personality traits. It reshapes the data, classifies drugs as legal or illegal, and generates multiple visualizations, including distribution pie charts and bar plots, drug-use histograms, personality trait boxplots, demographic-stratified heatmaps, and a word cloud of drug popularity among users. Through sidebar controls, users can filter drug types, select demographic facets, and choose personality traits to examine

TABLES CODING.Rmd: This file loads and cleans the drug-use dataset, generates descriptive tables stratified by gender, calculates p-values using chi-square or Fisher’s tests, creates composite legal and illegal drug-use outcomes, summarizes their prevalence across age and education groups, and fits logistic regression models to estimate adjusted odds ratios for personality traits associated with illegal drug use.

TABLES PROJECT.docx: Tables 1,2 and 3 output from TABLES CODING.Rmd

## Contributors
Tanya Budhiraja
Cami Diehl
Cesar Alas Pineda
Kenechukwu Sibeudu

## Software & Packages
R Version: R version 4.5.0

Packages Used: tidyverse, dplyr, readxl, janitor, nnet, ggplot2, shiny, tableone, broom

Other Tools: Excel (for data cleaning), Python (file format conversion)
