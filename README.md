# Cyclistic-Trip-Analysis-Project
#### This repository contains the comprehensive analysis of Cyclistic's historical trip data.


 ## Introduction:

Welcome to my portfolio! In this collection of work, I delve into a captivating case study centered around Cyclistic, a prominent bike-share company based in the bustling city of Chicago. As a junior data analyst on the marketing team at Cyclistic, my primary objective is to decipher how the usage patterns of annual members and casual riders differ, ultimately aiming to bolster the company's annual membership count.

The significance of this endeavor cannot be overstated, as the director of marketing firmly believes that Cyclistic's future prosperity hinges on maximizing annual memberships. To this end, my team and I embark on a comprehensive analysis of Cyclistic's historical trip data, meticulously examining the behaviors and preferences of both casual riders and annual members.

Our mission is twofold: first, to gain deep insights into the distinct usage patterns of these two customer segments, and second, to leverage these insights in crafting a compelling marketing strategy aimed at enticing casual riders to transition into loyal annual members.

However, the journey toward achieving our goals is not without its challenges. With Cyclistic executives poised to scrutinize and approve our recommendations, it is imperative that our insights are not only robust but also presented in a visually engaging and professional manner. Hence, our analysis is not merely an exercise in data exploration; it is a strategic endeavor to influence decision-making and drive Cyclistic's growth trajectory.

Join me as I navigate through the intricate layers of Cyclistic's data landscape, uncovering invaluable insights and crafting actionable recommendations that will propel the company towards sustained success.

## ASK Phase:

In this phase, we outline the key questions posed by Lily Moreno, the director of marketing at Cyclistic, and emphasize our focus on addressing the first question: How do annual members and casual riders use Cyclistic bikes differently?

## Guiding Questions Provided by Moreno:

#### 1. How do annual members and casual riders use Cyclistic bikes differently?
#### 2. Why would casual riders buy Cyclistic annual memberships?
#### 3. How can Cyclistic use digital media to influence casual riders to become members?

### Focus Question:
Our primary focus is on answering the first question posed by Lily Moreno. We aim to delve into Cyclistic's historical trip data to discern the disparities in bike usage patterns between annual members and casual riders. By understanding these differences, we can provide valuable insights that will inform the design of a targeted marketing strategy aimed at converting casual riders into loyal annual members.

### About the Company:
Cyclistic launched its bike-share program in 2016, quickly growing to a fleet of 5,824 bicycles spread across 692 stations in Chicago. The program's success is attributed to its flexible pricing plans, catering to both casual riders and annual members. While the program has attracted a diverse customer base, Moreno believes that maximizing annual memberships holds the key to future growth. To achieve this goal, she has tasked our team with analyzing trip data to uncover usage trends and preferences among different customer segments.

## PREPARE Phase:

In this phase, we describe the data sources used, detail how the data has been prepared for analysis, and ensure adherence to data privacy regulations.

## Data Sources:

##### The primary data source used for this analysis is historical trip data obtained from Cyclistic, a fictional bike-share company.
##### The data sets, although under different names, are appropriate for answering the business questions and have been made available by Motivate International Inc. under a suitable license agreement.
### Data Preparation Steps:

#### 1. Downloading and Storage: The historical trip data for the previous 12 months was downloaded from the provided link. The files were then stored appropriately on the local system.
#### 2. Organization: Upon download, the data files were organized into a structured folder hierarchy, ensuring ease of access and management throughout the analysis process.
#### 3. Sorting and Filtering: The data was sorted and filtered as necessary to facilitate further analysis. This involved identifying relevant variables and subsets of data that align with the research objectives.
#### 4. Data Integrity Verification: To ensure data integrity, various checks were performed, including verifying file completeness, assessing data consistency, and addressing any anomalies or discrepancies.
#### 5. Adherence to Data Privacy Regulations: Given the sensitivity of personal information, data privacy regulations were strictly adhered to. Personally identifiable information was handled with caution, and measures were taken to anonymize and aggregate the data appropriately.
### Deliverable:
A comprehensive description of all data sources used, along with details of the preparation process, will be documented to ensure transparency and reproducibility of the analysis.

## PROCESS Phase:

In this phase, we explain the tools chosen for analysis and data cleaning, describe the process of cleaning and manipulating the data to ensure its integrity, and provide documentation of the cleaning process.

## Tools Chosen:

##### For data analysis and manipulation, the R programming language and RStudio IDE were chosen due to their versatility and extensive libraries for data processing.
##### Specifically, the tidyverse package, which includes various packages like dplyr and tidyr, was utilized for its efficient data manipulation capabilities.

### Data Cleaning Process:

#### 1. Data Import: The historical trip data from Divvy 2019 Q1 and Divvy 2020 Q1 was imported into R using the read.csv() function.
#### 2. Column Renaming: Column names of divvy_2020_Q1 were renamed to match those of divvy_2019_Q1 for consistency using the colnames() function.
#### 3. Column Removal: The "member_casual" column, present only in divvy_2020_Q1, was removed to ensure consistency between the two data frames.
#### 4. Data Merging: The data frames divvy_2019_Q1 and divvy_2020_Q1 were merged into a single data frame named divvy_data using the rbind() function.
#### 5. Data Cleaning: Any necessary data cleaning steps, such as handling missing values or removing duplicates, were performed to ensure data integrity.
#### 6. Descriptive Analysis: Descriptive analysis, including summary statistics and data distribution, was conducted using the summary() function.

### Documentation:
The entire data cleaning process, including steps taken and transformations applied, was documented within the R script for review and sharing purposes.


### Deliverable:
A clean and well-prepared data set, along with documentation of the cleaning process, ensures that subsequent analysis and visualization tasks are based on reliable and consistent data. Additionally, the use of RStudio facilitates seamless integration of analysis code with documentation and visualization outputs.








