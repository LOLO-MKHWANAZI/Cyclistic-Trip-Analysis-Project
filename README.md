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

```R
# Install and load necessary packages
install.packages("tidyverse")
library(tidyverse)

# Importing data from Divvy 2019 Q1 and Divvy 2020 Q1
divvy_2019_Q1 <- read.csv("Divvy_Trips_2019_Q1.csv")
divvy_2020_Q1 <- read.csv("Divvy_Trips_2020_Q1.csv")

# Check column names of divvy_2019_Q1 and divvy_2020_Q1
print(colnames(divvy_2019_Q1))
print(colnames(divvy_2020_Q1))

# Rename columns of divvy_2020_Q1 to match the column names of divvy_2019_Q1
colnames(divvy_2020_Q1) <- c("trip_id", "start_time", "end_time", "bikeid", "tripduration",
                             "from_station_id", "from_station_name", "to_station_id", "to_station_name",
                             "usertype", "gender", "birthyear")

# Remove the "member_casual" column from divvy_2020_Q1
divvy_2020_Q1 <- divvy_2020_Q1[, -which(names(divvy_2020_Q1) == "member_casual")]

# Check if both data frames have the same number of columns now
print(ncol(divvy_2019_Q1))
print(ncol(divvy_2020_Q1))

# Making columns consistent and merging them into a single data frame
divvy_data <- rbind(divvy_2019_Q1, divvy_2020_Q1)

# Cleaning up and preparing data for analysis
# Specific cleaning steps:

# Handle missing values, if any
divvy_data <- na.omit(divvy_data)

# Remove duplicates, if any
divvy_data <- unique(divvy_data)

# Convert data types if needed (e.g., converting character columns to factors, datetime conversion)
divvy_data$start_time <- as.POSIXct(divvy_data$start_time, format = "%Y-%m-%d %H:%M:%S")
divvy_data$end_time <- as.POSIXct(divvy_data$end_time, format = "%Y-%m-%d %H:%M:%S")

# Convert tripduration to numeric
divvy_data$tripduration <- as.numeric(divvy_data$tripduration)

# Check for any non-numeric values in tripduration
non_numeric_tripduration <- divvy_data[!grepl("^\\d+\\.?\\d*$", divvy_data$tripduration), "tripduration"]
print(non_numeric_tripduration)

# Remove non-numeric values from tripduration (if any)
divvy_data <- divvy_data[grepl("^\\d+\\.?\\d*$", divvy_data$tripduration), ]

# Now, perform the visualization
# Visualization 1: Comparing Trip Duration
ggplot(data = divvy_data, aes(x = usertype, y = tripduration/60)) +
  geom_boxplot(fill = "skyblue") +
  labs(title = "Comparison of Trip Duration",
       x = "User Type",
       y = "Trip Duration (minutes)") +
  theme_minimal()

# Visualization 2: Trip Count by User Type
trip_count <- divvy_data %>% group_by(usertype) %>% summarize(count = n())
ggplot(data = trip_count, aes(x = usertype, y = count, fill = usertype)) +
  geom_bar(stat = "identity") +
  labs(title = "Trip Count by User Type",
       x = "User Type",
       y = "Trip Count") +
  theme_minimal()

# Visualization 3: Gender Distribution among Users
gender_count <- divvy_data %>% filter(!is.na(gender)) %>% group_by(usertype, gender) %>% summarize(count = n())
ggplot(data = gender_count, aes(x = usertype, y = count, fill = gender)) +
  geom_bar(stat = "identity", position = "dodge") +
  labs(title = "Gender Distribution among Users",
       x = "User Type",
       y = "Count",
       fill = "Gender") +
  theme_minimal()

# Visualization 4: Age Distribution among Users
current_year <- as.numeric(format(Sys.Date(), "%Y"))
divvy_data$age <- current_year - divvy_data$birthyear
age_data <- divvy_data %>% filter(!is.na(age))
ggplot(data = age_data, aes(x = usertype, y = age, fill = usertype)) +
  geom_boxplot() +
  labs(title = "Age Distribution among Users",
       x = "User Type",
       y = "Age") +
  theme_minimal()

# Example: Plotting a histogram of trip durations
ggplot(data = divvy_data, aes(x = tripduration)) +
  geom_histogram(binwidth = 100, fill = "skyblue", color = "black", stat = "count") +
  labs(title = "Distribution of Trip Durations",
       x = "Trip Duration (seconds)",
       y = "Frequency") +
  theme_minimal()

# Specify the relative file path for exporting summary statistics
file_path <- "summary_file.csv"

# Exporting a summary file for further analysis
write.csv(summary(divvy_data), file_path)

# Save cleaned data
write.csv(divvy_data, "cleaned_divvy_data.csv", row.names = FALSE)

```
- This script first loads necessary libraries and imports the Divvy trip data from 2019 Q1 and 2020 Q1. Then, it cleans the data by renaming columns, removing unnecessary columns, handling missing values, removing duplicates, converting data types, and visualizing various aspects of the data using ggplot2. Finally, it exports summary statistics and the cleaned data to CSV files.

### Deliverable:
A clean and well-prepared data set, along with documentation of the cleaning process, ensures that subsequent analysis and visualization tasks are based on reliable and consistent data. Additionally, the use of RStudio facilitates seamless integration of analysis code with documentation and visualization outputs.


## To ***analyze*** the data effectively, the following steps were taken:

#### Data Import: Historical trip data from Divvy 2019 Q1 and Divvy 2020 Q1 was imported into R using the read.csv() function.

#### Making Columns Consistent and Merging: Column names of Divvy 2020 Q1 were renamed to match those of Divvy 2019 Q1 for consistency. Then, the two data frames were merged into a single data frame named divvy_data using the rbind() function.

#### Cleaning and Preparing Data: Any necessary data cleaning steps, such as handling missing values or removing duplicates, were performed to ensure data integrity. No specific cleaning steps were shown in the provided example.

#### Descriptive Analysis: Descriptive analysis was conducted using the summary() function to understand the data distribution and summary statistics.

#### Exporting Summary File: Summary statistics were exported to a CSV file for further analysis using the write.csv() function.

- Additionally, calculations can be performed based on specific business questions or analysis objectives. For example, calculations related to average trip duration, frequency of bike usage by user type, or seasonal variations in bike rentals can provide valuable insights into user behavior and preferences.

- Regarding trends or relationships identified in the data, these could include patterns in bike usage based on user type, popular biking routes or stations, peak usage hours, or differences in usage between different months or seasons.

- These insights can help answer the guiding questions provided in the case study, such as understanding how annual members and casual riders use Cyclistic bikes differently and identifying factors that may influence casual riders to become annual members.

## "Share" phase based on the key findings derived from the analysis of Cyclistic's historical trip data:

### Creation of Visualizations to Communicate Findings Effectively:

Visualizations play a crucial role in conveying insights effectively to the executive team. By presenting the key findings through sophisticated and polished visualizations, we can ensure that the information is easily understandable and actionable.

### Process of Creating Visualizations Using Various Tools:

#### **1. Selection of Visualization Tools:** We'll use R programming language with ggplot2 package for creating visualizations due to its versatility and ability to generate high-quality plots.

#### 2. Data Preparation: Before creating visualizations, we'll organize the data and prepare it for visualization by aggregating, summarizing, and formatting it appropriately.

#### 3. Choosing Visual Forms: Based on the key findings, we'll select appropriate visual forms such as bar charts, histograms, and pie charts to represent trip duration, trip count, gender distribution, and age distribution.

#### 4. Creating Visualizations: Using ggplot2 in R, we'll create visually appealing and informative plots that effectively communicate the key findings. Each visualization will be carefully designed to highlight the relevant insights.

### Supporting Visualizations and Key Findings Derived from the Analysis:

#### 1. Trip Duration Comparison: We'll create a box plot or a violin plot to compare the distribution of trip durations between annual members and casual riders. This visualization will clearly illustrate any differences in usage patterns.

#### 2. Trip Count Disparity: A bar chart or a pie chart can be used to visualize the proportion of trips contributed by annual members and casual riders. This will highlight the disparity in engagement with the service between the two user groups.

#### 3. Gender Distribution: A pie chart or a bar chart can show the gender distribution among Cyclistic users, with separate segments or bars representing male and female users. This will visually depict the gender disparity observed in the data.

#### 4. Age Distribution: A histogram or a density plot can represent the age distribution of Cyclistic users, with separate distributions for annual members and casual riders. This visualization will reveal any differences in the age demographics of the two user groups.


![d5711383-a881-49a7-a842-d2f613d7d065](https://github.com/LOLO-MKHWANAZI/Cyclistic-Trip-Analysis-Project/assets/163551783/96c53af0-544d-40c1-8357-5c1d5951762f)

![eea9e4d1-4da4-498d-9754-dae238dfb7d8](https://github.com/LOLO-MKHWANAZI/Cyclistic-Trip-Analysis-Project/assets/163551783/a4a751b0-3b29-4c26-9d65-a274b6d2766f)

![cc109b72-1490-4767-a3c7-2795399395fb](https://github.com/LOLO-MKHWANAZI/Cyclistic-Trip-Analysis-Project/assets/163551783/7d04cf6e-716b-4bde-b2fe-c4c93ea683a6)








- By presenting these visualizations along with the key findings, we can effectively communicate insights to the executive team, facilitating informed decision-making and strategy development for Cyclistic.







