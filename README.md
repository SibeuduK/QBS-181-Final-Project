# Final Project: Personality Traits and Drug Use Patterns in the UCI Drug Consumption Dataset


## Project Overview
This project examines associations between demographic characteristics, personality traits (Big Five, impulsivity, sensation seeking), and legal/illegal drug use using the UCI ML Repository’s “Drug Consumption (Quantified)” dataset.

Our goals were to:

Clean the dataset, generate descriptive statistics (Table 1 & Table 2), build multivariable logistic regression models to examine illegal drug use, and produce an interactive visualization dashboard using R Shiny. 

This README documents the entire data-wrangling and analysis pipeline so that any new user can fully reproduce the project.

## Data Sources
Dataset: Drug Consumption (Quantified) — UCI Machine Learning Repository

Original format: .ARFF

Converted to .csv using Python 

Working Data File: CLEANING DATA DRUG.xlsx

Contains: Demographics, Personality trait scores, Drug use variables, Raw categorical encodings 

## Repository Structure
CLEANING DATA DRUG.xlsx — Dataset with standardized variable names and recoded demographic labels, used as the input for all analyses.
FinalProject.Rmd — data import, cleaning pipeline, variable creation, regression models, and final outputs.
TABLES CODING.Rmd — Script used to generate Table 1 and Table 2 (descriptive statistics and drug-use prevalence tables).
RShiny.Rmd — Code for the interactive R Shiny dashboard visualizing patterns in personality traits and drug use.
cleaned_dataset.csv — Fully processed, analysis ready dataset after cleaning.

## Software & Packages
R Version: R version 4.5.0

Packages Used: tidyverse, dplyr, readxl, janitor, nnet, ggplot2, shiny, tableone, broom

Other Tools: Excel (for 1st cleaning), Python (format conversion)


### Excel Cleaning

- done in CLEANING DATA DRUG.xlsx

- standardized variable names for readability

- Replaced numeric coded demographics with meaningful labels

- Education categorized into Low / Medium / High

- Removed unused variables

- Verified no duplicate participant entries

- Checked for impossible values or bad entries



### Cleaning Pipeline in 

#### Handling Missing Data

ensured no missing data

made sure no variable contained impossible values

#### Recoding Variables

Personality trait scores converted into Low / Medium / High categories

Drug use put into categories: User vs Non user

Any legal drug use = caffeine OR nicotine OR alcohol OR chocolate

Any illegal drug use = cocaine OR ketamine OR heroin OR LSD

#### Creating Final Analysis Dataset

Selected only required variables

Ensured factors were properly ordered


### Table Creation
Table 1 — Demographic & Personality Profile by Gender

Generated using tableone in TABLES CODING.Rmd

Variables included: Age group, Education, Ethnicity, Country, Big Five personality traits, Impulsivity, Sensation Seeking, Individual drug use variables

Table 2 — Legal/Illegal Drug Use by Age & Education, Chi-square, Fisher’s test

### Regression Modeling

in FinalProject.Rmd:

Logistic regression predicting any illegal drug use

Adjusted for: Gender, Age group, Education

Output ORs + 95% CI extracted into Table 3


### Interactive Dashboard

In RShiny.Rmd:

Dashboard includes: explore drug use by demographic group, personality trait distributions, prevalence of each drug

Filters for gender, age, education

## Reproducibility 

reproduce the pipeline by following:

clone this repository

place raw Excel file in data/

run FinalProject.Rmd 

run TABLES CODING.Rmd to regenerate Tables 1 & 2

run RShiny.Rmd and run the dashboard



## Contributors

Tanya Budhiraja
Cesar Alas
Kenechukwu Sibeudu 
Cameron Diehl
