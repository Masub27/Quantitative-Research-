<!--

author:   André Dietrich
email:    masub.makhdoom@ovgu.de
date:     29/03/2025
version:  30.0.0
language: en
narrator: UK English Female

repository: https://github.com/LiaScript/docs

logo:     img/logo.png

comment:  This document shall provide an entire compendium and course on the
          development of Open-courSes with [LiaScript](https://LiaScript.github.io).
          As the language and the systems grows, also this document will be updated.
          Feel free to fork or copy it, translations are very welcome...

script:   https://cdn.jsdelivr.net/chartist.js/latest/chartist.min.js
          https://felixhao28.github.io/JSCPP/dist/JSCPP.es5.min.js

link:     https://cdn.jsdelivr.net/chartist.js/latest/chartist.min.css

link:     https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css

import:   https://raw.githubusercontent.com/liaTemplates/ABCjs/main/README.md

link:     https://fonts.googleapis.com/css2?family=Noto+Sans+Egyptian+Hieroglyphs
          https://fonts.googleapis.com/css2?family=Noto+Sans+Ogham

font:     Noto Sans Egyptian Hieroglyphs, Noto Sans Ogham
-->

# R Project Material for Training
Creating Prompt to write an R Example script reading CSV File
 
Claude Prompt: 

* I have an Rproject file which has as a parent folder called "R_project". In the folder as well exists a csv file called 2024_25_Quant_Example_Data_AI_Competency.csv

* Please write me an R script which loads the 2024_25_Quant_Example_Data_AI_Competency.csv into the R environment.

Output from Claude: 

I'll help you write an R script to load your CSV file. Since the file is in the same directory as your R project, we can use relative paths.

```r
# Load required packages
library(readr)  # For reading CSV files
library(here)   # For project-relative paths

# Set working directory to project root (not always necessary with RProject, but good practice)
setwd(here::here())

# Read the CSV file
ai_competency_data <- read_csv("2024_25_Quant_Example_Data_AI_Competency.csv")

# Display the first few rows of the data
head(ai_competency_data)

# Display basic information about the dataset
glimpse(ai_competency_data)

```

This script:
1. Loads necessary packages
2. Uses the `here` package to ensure reliable path handling within your R project
3. Reads the CSV file into a data frame called `ai_competency_data`
4. Includes commands to preview the data

Before running this script, make sure you have the required packages installed. If you don't, you can install them using:

```r
install.packages(c("readr", "here"))
```

Would you like me to add any additional data validation or processing steps to the script?

Output script: (R file you have to create)


# Load required packages
library(readr)  # For reading CSV files
library(here)   # For project-relative paths

# Set working directory to project root (not always necessary with RProject, but good practice)
setwd(here::here())

# Read the CSV file
ai_competency_data <- read_csv("2024_25_Quant_Example_Data_AI_Competency.csv")

# Display the first few rows of the data
head(ai_competency_data)

# Display basic information about the dataset
glimpse(ai_competency_data)
