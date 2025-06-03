<!--
author:   Masub Makhdoom
email:    masub.makhdoom@ovgu.de
version:  1.0.0
language: en
narrator: US English Female

comment:  This presentation covers fundamental concepts and practical techniques for reading and manipulating data in R.

script:   https://cdn.jsdelivr.net/pyodide/v0.24.1/full/pyodide.js
import:   https://raw.githubusercontent.com/LiaScript/CodeRunner/master/README.md
-->

# Descriptive Data Analysis in R

## Introduction

Descriptive data analysis provides essential insights into data characteristics through statistical summaries and visualizations. In quantitative research, these methods help researchers understand data distribution, identify patterns, and validate data quality. Proper descriptive analysis forms the foundation for inferential statistics and hypothesis testing.

## 1. Measures of Central Tendency

### Use in Data Evaluation and Interpretation

* Enables identification of typical values and data concentration
* Facilitates comparison between different groups or datasets
* Helps detect potential data entry errors or outliers
* Provides basis for further statistical analyses

### Practical Tips
   --{{0}}--
!?[](https://github.com/Masub27/Quantitative-Research-/blob/main/Measures%20of%20Central%20TTendency.mp4?raw=true)

1. **Choose Appropriate Measure**: Mean for normal distributions, median for skewed data
2. **Handle Missing Values**: Explicitly state how missing values are handled
3. **Consider Outliers**: Assess impact of outliers on central tendency measures
> "Shakira  is here to help us understand this better."

### R Example

```r
# Load required libraries and data
library(readr)
library(dplyr)

# Read the data
data <- read_csv("https://raw.githubusercontent.com/HTegelbeckers/Teaching/refs/heads/main/2024_25_Quant_Example_Data_AI_Competency.csv")

# Calculate basic measures of central tendency for variables v_84 to v_89
central_measures <- data %>%
  select(v_84, v_85, v_86, v_87, v_88, v_89) %>%
  summarise(across(everything(),
                  list(mean = ~mean(., na.rm = TRUE),
                       median = ~median(., na.rm = TRUE),
                       mode = ~as.numeric(names(which.max(table(.))))
                  )))

print(central_measures)
```
@LIA.r_withShell

### Task

Calculate measures of central tendency (mean, median, and mode) for the variable `v_84` and create a summary table. Compare these measures and explain what they tell us about the distribution of the data.

### Solution

```r
# Calculate central tendency measures for v_84
# Load required libraries and data
library(readr)
library(dplyr)

# Read the data
data <- read_csv("https://raw.githubusercontent.com/HTegelbeckers/Teaching/refs/heads/main/2024_25_Quant_Example_Data_AI_Competency.csv")

v84_summary <- data %>%
  summarise(
    mean_v84 = mean(v_84, na.rm = TRUE),
    median_v84 = median(v_84, na.rm = TRUE),
    mode_v84 = as.numeric(names(which.max(table(v_84))))
  )

# Create comparison table
v84_stats <- data.frame(
  Measure = c("Mean", "Median", "Mode"),
  Value = unlist(v84_summary)
)

print(v84_stats)

# Create histogram to visualize distribution
hist(data$v_84, main="Distribution of v_84", xlab="Values", breaks=10)
```
@LIA.r_withShell

### Interpretation Tips

* If mean ≈ median: Distribution might be symmetrical
* Mean > median: Right-skewed distribution
* Mean < median: Left-skewed distribution
* Multiple modes: Possible bimodal or multimodal distribution

## 2. Measures of Variability (Dispersion)

### Introduction

Measures of variability quantify how spread out data points are in a dataset. These measures are crucial for understanding data distribution and variability, providing insights into data reliability and consistency. They complement central tendency measures by describing how well these averages represent the dataset.

### Use in Data Evaluation and Interpretation

* Assesses data consistency and reliability
* Identifies potential outliers and unusual patterns
* Enables comparison of variability between different datasets
* Helps evaluate the precision of measurements

### Practical Tips
   --{{0}}--
!?[](https://github.com/Masub27/Quantitative-Research-/blob/main/Measures%20of%20Variability%20Dispersionn.mp4?raw=true)

1. **Choose Appropriate Measure**: Use standard deviation for normal distributions, IQR for skewed data
2. **Context Matters**: Consider the scale and units of your data
3. **Outlier Impact**: Assess how outliers affect variability measures
> "Nora  is here to help us understand this better."

### R Example

```r
# Calculate measures of variability
library(readr)
library(dplyr)

# Read the data
data <- read_csv("https://raw.githubusercontent.com/HTegelbeckers/Teaching/refs/heads/main/2024_25_Quant_Example_Data_AI_Competency.csv")

# Calculate variability measures for variables v_84 to v_89
variability_measures <- data %>%
  select(v_84, v_85, v_86, v_87, v_88, v_89) %>%
  summarise(across(everything(),
                  list(sd = ~sd(., na.rm = TRUE),
                       var = ~var(., na.rm = TRUE),
                       IQR = ~IQR(., na.rm = TRUE),
                       range = ~diff(range(., na.rm = TRUE))
                  )))

print(variability_measures)
```
@LIA.r_withShell

### Task

Calculate the coefficient of variation (CV = standard deviation / mean) for variables v_84 to v_89 to compare their relative variability.

### Solution

```r
# Load required libraries and data
library(readr)
library(dplyr)

# Read the data
data <- read_csv("https://raw.githubusercontent.com/HTegelbeckers/Teaching/refs/heads/main/2024_25_Quant_Example_Data_AI_Competency.csv")

# Calculate coefficient of variation
cv_analysis <- data %>%
  select(v_84, v_85, v_86, v_87, v_88, v_89) %>%
  summarise(across(everything(),
                  ~sd(., na.rm = TRUE) / mean(., na.rm = TRUE) * 100)) %>%
  round(2)

print("Coefficient of Variation (%):")
print(cv_analysis)
```
@LIA.r_withShell

## 3. Measures of Relative Position

### Introduction

Measures of relative position help understand where specific values fall within the overall distribution of a dataset. These measures provide context for individual observations and help identify unusual or extreme values in your data.

### Use in Data Evaluation and Interpretation

* Identifies data distribution and skewness
* Helps detect outliers and extreme values
* Enables comparison of values across different datasets
* Facilitates understanding of data quartiles and percentiles

### Practical Tips
   --{{0}}--
!?[](https://github.com/Masub27/Quantitative-Research-/blob/main/Measures%20of%20Relative%20Positionnn.mp4?raw=true)

1. **Percentile Choice**: Select appropriate percentiles based on your analysis needs
2. **Outlier Detection**: Use quartiles for identifying outliers
3. **Data Visualization**: Combine with box plots for better visualization
> "Omar  is here to help us understand this better."

### R Example

```r
# Calculate relative position measures
library(readr)
library(dplyr)

# Read the data
data <- read_csv("https://raw.githubusercontent.com/HTegelbeckers/Teaching/refs/heads/main/2024_25_Quant_Example_Data_AI_Competency.csv")

# Calculate quartiles and percentiles for variables v_84 to v_89
position_measures <- data %>%
  select(v_84, v_85, v_86, v_87, v_88, v_89) %>%
  summarise(across(everything(),
                  list(q1 = ~quantile(., 0.25, na.rm = TRUE),
                       median = ~quantile(., 0.5, na.rm = TRUE),
                       q3 = ~quantile(., 0.75, na.rm = TRUE),
                       p90 = ~quantile(., 0.9, na.rm = TRUE)
                  )))

print(position_measures)
```
@LIA.r_withShell

### Task

Create a box plot for variables v_84 to v_89 and identify the values that fall outside the 1.5 * IQR range (potential outliers).

### Solution

```r
# Load required libraries and data
library(readr)
library(dplyr)

# Read the data
data <- read_csv("https://raw.githubusercontent.com/HTegelbeckers/Teaching/refs/heads/main/2024_25_Quant_Example_Data_AI_Competency.csv")
# Create box plot
boxplot(data[, c("v_84", "v_85", "v_86", "v_87", "v_88", "v_89")],
        main = "Distribution of Variables",
        col = "lightblue",
        ylab = "Values")

# Function to identify outliers
identify_outliers <- function(x) {
  q1 <- quantile(x, 0.25, na.rm = TRUE)
  q3 <- quantile(x, 0.75, na.rm = TRUE)
  iqr <- q3 - q1
  upper <- q3 + 1.5 * iqr
  lower <- q1 - 1.5 * iqr
  return(x[x < lower | x > upper])
}

# Apply function to each variable
outliers <- lapply(data[, c("v_84", "v_85", "v_86", "v_87", "v_88", "v_89")], 
                  identify_outliers)

print("Outliers for each variable:")
print(outliers)
```
@LIA.r_withShell

## 4. Graphical Methods

### Introduction

Graphical methods provide visual representations of data distributions and relationships. These visual techniques are essential for quickly understanding patterns, trends, and anomalies in data that might not be immediately apparent through numerical summaries.

### Use in Data Evaluation and Interpretation

* Visualizes data distribution and patterns
* Identifies relationships between variables
* Detects outliers and unusual patterns
* Communicates findings effectively to non-technical audiences

### Practical Tips
   --{{0}}--
!?[](https://github.com/Masub27/Quantitative-Research-/blob/main/Graphical%20Methods.mp4?raw=true)


1. **Choose Appropriate Plot**: Select visualization based on data type and analysis goal
2. **Clear Labeling**: Include clear titles, axes labels, and legends
3. **Color Usage**: Use colors effectively to highlight important patterns
> "Ayaan  is here to help us understand this better."
### R Example

```r
# Create various plots
library(readr)
library(ggplot2)
library(tidyr)

# Read the data
data <- read_csv("https://raw.githubusercontent.com/HTegelbeckers/Teaching/refs/heads/main/2024_25_Quant_Example_Data_AI_Competency.csv")

# Create histogram
ggplot(data, aes(x = v_84)) +
  geom_histogram(fill = "lightblue", color = "black", bins = 30) +
  labs(title = "Distribution of v_84",
       x = "Values",
       y = "Frequency")

# Create scatter plot
ggplot(data, aes(x = v_84, y = v_85)) +
  geom_point() +
  labs(title = "Relationship between v_84 and v_85",
       x = "v_84",
       y = "v_85")
```
@LIA.r_withShell

### Task

Create a correlation matrix visualization for variables v_84 to v_89 using a heatmap.

### Solution

```r
# Create correlation matrix
# Load required libraries and data
library(readr)
library(dplyr)

# Read the data
data <- read_csv("https://raw.githubusercontent.com/HTegelbeckers/Teaching/refs/heads/main/2024_25_Quant_Example_Data_AI_Competency.csv")
library(corrplot)

corr_matrix <- cor(data[, c("v_84", "v_85", "v_86", "v_87", "v_88", "v_89")],
                  use = "complete.obs")

# Create correlation plot
corrplot(corr_matrix, 
         method = "color",
         type = "upper",
         addCoef.col = "black",
         tl.col = "black",
         tl.srt = 45,
         diag = FALSE)
```
@LIA.r_withShell

## 5. Frequency Distribution

### Introduction

Frequency distribution analysis organizes data into categories and shows how often each value occurs. This method is fundamental for understanding data patterns and identifying the most common values or ranges in your dataset.

### Use in Data Evaluation and Interpretation

* Summarizes data distribution effectively
* Identifies most and least common values
* Helps detect patterns and trends
* Facilitates comparison between different groups

### Practical Tips
   --{{0}}--
!?[](https://github.com/Masub27/Quantitative-Research-/blob/main/Frequency%20Distribution.mp4?raw=true)

1. **Bin Width**: Choose appropriate bin sizes for continuous data
2. **Categories**: Create meaningful categories for categorical data
3. **Visualization**: Use appropriate charts based on data type
> "Sara is here to help us understand this better."

### R Example

```r
library(readr)
library(dplyr)
library(ggplot2)

# Read the data
data <- read_csv("https://raw.githubusercontent.com/HTegelbeckers/Teaching/refs/heads/main/2024_25_Quant_Example_Data_AI_Competency.csv")

# Create frequency table for v_84
freq_table <- table(data$v_84)
print("Frequency Table:")
print(freq_table)

# Create relative frequency table
rel_freq <- prop.table(freq_table) * 100
print("\nRelative Frequency (%):")
print(round(rel_freq, 2))

# Visualize frequency distribution
ggplot(data, aes(x = factor(v_84))) +
  geom_bar() +
  labs(title = "Frequency Distribution of v_84",
       x = "Values",
       y = "Frequency")
```
@LIA.r_withShell

### Task

Create a cumulative frequency distribution plot for v_84 and identify the median value using the plot.

### Solution

```r
# Load required libraries and data
library(readr)
library(dplyr)

# Read the data
data <- read_csv("https://raw.githubusercontent.com/HTegelbeckers/Teaching/refs/heads/main/2024_25_Quant_Example_Data_AI_Competency.csv")

# Calculate cumulative frequencies
cum_freq <- data %>%
  group_by(v_84) %>%
  summarise(count = n()) %>%
  arrange(v_84) %>%
  mutate(cumulative = cumsum(count),
         relative_cumulative = cumulative / sum(count) * 100)

# Create cumulative frequency plot
ggplot(cum_freq, aes(x = v_84, y = relative_cumulative)) +
  geom_line() +
  geom_point() +
  geom_hline(yintercept = 50, linetype = "dashed", color = "red") +
  labs(title = "Cumulative Frequency Distribution of v_84",
       x = "Values",
       y = "Cumulative Percentage (%)")
```
@LIA.r_withShell

## 6. Data Cleaning and Preparation

### Introduction

Data cleaning and preparation are crucial steps that ensure the quality and reliability of your analysis. These processes involve identifying and handling missing values, outliers, and inconsistencies in your dataset.

### Use in Data Evaluation and Interpretation

* Ensures data quality and reliability
* Identifies and handles missing values appropriately
* Detects and manages outliers
* Standardizes data format and coding

### Practical Tips
   --{{0}}--
!?[](https://github.com/Masub27/Quantitative-Research-/blob/main/Data%20Cleaning%20and%20Preparation.mp4?raw=true)


1. **Document Changes**: Keep track of all data cleaning steps
2. **Validate Results**: Check data before and after cleaning
3. **Preserve Raw Data**: Always keep a copy of the original dataset
> " Emma is here to help us understand this better."
### R Example

```r
library(readr)
library(dplyr)
library(tidyr)

# Read the data
data <- read_csv("https://raw.githubusercontent.com/HTegelbeckers/Teaching/refs/heads/main/2024_25_Quant_Example_Data_AI_Competency.csv")

# Check missing values
missing_values <- colSums(is.na(data))
print("Missing Values per Column:")
print(missing_values)

# Check outliers using z-scores
z_scores <- scale(data[, c("v_84", "v_85", "v_86", "v_87", "v_88", "v_89")])
outliers <- which(abs(z_scores) > 3, arr.ind = TRUE)
print("\nPotential Outliers (|z-score| > 3):")
print(outliers)

# Basic data cleaning
clean_data <- data %>%
  mutate(across(c(v_84:v_89), 
                ~ifelse(abs(scale(.)) > 3, NA, .))) %>%
  na.omit()

print("\nDimensions after cleaning:")
print(dim(clean_data))
```
@LIA.r_withShell

### Task

Identify and handle missing values in variables v_84 to v_89 using multiple imputation techniques.

### Solution

```r
# Load required libraries and data
library(mice)
library(readr)
library(dplyr)

# Read the data
data <- read_csv("https://raw.githubusercontent.com/HTegelbeckers/Teaching/refs/heads/main/2024_25_Quant_Example_Data_AI_Competency.csv")

# Select variables for imputation
vars_to_impute <- c("v_84", "v_85", "v_86", "v_87", "v_88", "v_89")

# Perform multiple imputation
imputed_data <- mice(data[vars_to_impute], m=5, maxit=50, method='pmm', seed=500)

# Get completed dataset
completed_data <- complete(imputed_data, 1)

# Compare original and imputed data
summary_comparison <- rbind(
  summary(data[vars_to_impute]),
  summary(completed_data)
)

print("Summary Comparison (Original vs Imputed):")
print(summary_comparison)
```
@LIA.r_withShell

## 7. Data Exploration

### Introduction

Data exploration is an iterative process of investigating and analyzing datasets to discover patterns, relationships, and anomalies. It combines various statistical and visualization techniques to gain comprehensive insights into your data.

### Use in Data Evaluation and Interpretation

* Uncovers hidden patterns and relationships
* Identifies potential research questions
* Guides selection of appropriate statistical methods
* Validates data quality and assumptions

### Practical Tips
   --{{0}}--
!?[](https://github.com/Masub27/Quantitative-Research-/blob/main/Data%20Exploration.mp4?raw=true)


1. **Systematic Approach**: Follow a structured exploration process
2. **Multiple Techniques**: Combine different analytical methods
3. **Document Findings**: Keep track of all discoveries and insights

> "Max is here to help us understand this better."

### R Example

```r
library(readr)
library(dplyr)
library(ggplot2)
library(corrplot)

# Read the data
data <- read_csv("https://raw.githubusercontent.com/HTegelbeckers/Teaching/refs/heads/main/2024_25_Quant_Example_Data_AI_Competency.csv")

# Basic summary statistics
summary_stats <- summary(data[, c("v_84", "v_85", "v_86", "v_87", "v_88", "v_89")])
print("Summary Statistics:")
print(summary_stats)

# Correlation analysis
cor_matrix <- cor(data[, c("v_84", "v_85", "v_86", "v_87", "v_88", "v_89")],
                 use = "complete.obs")
print("\nCorrelation Matrix:")
print(round(cor_matrix, 2))

# Create visualization
pairs(data[, c("v_84", "v_85", "v_86", "v_87", "v_88", "v_89")])
```
@LIA.r_withShell

### Task

Conduct a comprehensive exploratory data analysis of variables v_84 to v_89, including distribution analysis, relationship patterns, and potential outliers.

### Solution

```r
# Load required libraries and data
library(readr)
library(dplyr)

# Read the data
data <- read_csv("https://raw.githubusercontent.com/HTegelbeckers/Teaching/refs/heads/main/2024_25_Quant_Example_Data_AI_Competency.csv")

# Comprehensive EDA
library(psych)

# Descriptive statistics
describe(data[, c("v_84", "v_85", "v_86", "v_87", "v_88", "v_89")])

# Distribution plots
par(mfrow=c(2,3))
for(var in c("v_84", "v_85", "v_86", "v_87", "v_88", "v_89")) {
  hist(data[[var]], main=paste("Distribution of", var),
       xlab=var, col="lightblue")
}

# Correlation plot
corrplot(cor_matrix, method="color", type="upper",
         addCoef.col="black", tl.col="black", tl.srt=45)

# Box plots for outlier detection
boxplot(data[, c("v_84", "v_85", "v_86", "v_87", "v_88", "v_89")],
        main="Distribution and Outliers",
        col="lightblue")
```
@LIA.r_withShell