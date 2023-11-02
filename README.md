# Attention Task Behavioral Performance Data Analysis (IOR)

This project performs an analysis of behavioral data obtained from a visual attention shifting task. The data includes observations for each participant who completed the task and details for each trial. The variables of interest include the trial number (`trialNum`), duration the participant had to orient, engage, and disengage attention (`ISIadj`), the number of attention shifts required to attend to the target digit (`targetIndex`), participant accuracy (`correct`), and the number of staircase reversals completed for each trial type (`nReversals`).

## Table of Contents

- [Load Packages](#load-packages)
- [Import Data](#import-data)
- [Data Cleaning](#data-cleaning)
- [Figures](#figures)

## Load Packages

The analysis is carried out using various R packages for statistics, data import, data visualization, and data manipulation. Some of the key packages used include:
- `psych`: For statistical analysis
- `readr`: For importing data
- `Hmisc`: For plotting
- `Rmisc`: For standard error calculation
- `readxl`: For reading Excel files
- `tidyverse`: A collection of packages for data science
- `plyr`, `ez`, `statmod`, `ggplot2`: Additional packages for statistical operations and plotting.

The packages can be installed in R using the install.packages("package_name") command.

## Import Data

The script begins by importing the behavioral data from the CSV file named "visual_shifting_ior_control_data.csv".

```R
behavioral_data <- read.csv(file = "visual_shifting_ior_control_data.csv")
```

## Data Cleaning

After data import, the cleaning process involves filtering trials not at threshold (where `nReversal != 0`). Additionally, some data transformations are conducted: converting `ISIadj` to milliseconds and changing `targetIndex` to a factor for categorical representation.

```R
behavioral_data_clean <- behavioral_data %>% filter(nReversal != 0)
behavioral_data_clean$ISIms <- behavioral_data_clean$ISIadj * 1000
behavioral_data_clean$targetIndex <- as.factor(behavioral_data_clean$targetIndex)
```

## Figures

This section generates a figure to illustrate the mean shifting speed for each participant and target index. It uses group summarization and error bar plotting to represent the mean performance per condition. The error bars are calculated for within-subject standard error (Morey, 2008) using the `Rmisc` package.

The figure is created using `ggplot2` and demonstrates the mean performance per condition, with points indicating participant means and error bars representing within-subject standard errors.

![performance](https://github.com/patzacher/attention_task_analysis_ior/assets/71090911/e929ba83-4956-4008-9824-796ee73856b6)

## Contributing
Contributions to this project are welcome. If you'd like to contribute, please follow these steps:

Fork the repository.

Create a new branch for your feature.

Make your changes and submit a pull request.
