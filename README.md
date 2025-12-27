Star Wars Survey Data Wrangling
Overview

This project focuses on cleaning and preparing the Star Wars Survey dataset for analysis.
The original dataset contains inconsistent column names, missing values, encoding issues, and mixed data types that make analysis difficult.

The goal of this data-wrangling process is to:

Standardize column names

Handle missing values

Convert survey responses into analysis-ready formats

Validate ranking data

Create meaningful demographic categories

Export a clean dataset for further analysis and visualization

Dataset

Source: Star Wars fan survey

File: StarWars.csv

Encoding: cp1252 (required due to special characters)

Type: Survey data (categorical, ordinal, demographic)

Data Wrangling Steps
1. Data Loading

Loaded the dataset using pandas.read_csv

Explicitly specified cp1252 encoding to handle non-UTF8 characters

Configured pandas to display all columns for easier inspection

2. Column Renaming

The original dataset included:

Multiple Unnamed columns

Multi-row headers

Encoding artifacts in column names

Actions taken:

Renamed all columns to meaningful, descriptive names

Fixed encoding issues (e.g., malformed characters in column names)

Standardized naming for movie rankings and character familiarity columns

3. Handling Missing Values

Certain columns were identified as essential:

RespondentID

Whether the respondent has seen Star Wars films

Gender

Age

Rows missing any of these values were removed using:

dropna(subset=important_cols)


This ensured the dataset retained only valid and usable survey responses.

4. Movie Viewing Columns (Yes / No Conversion)

The survey recorded movie viewing as text values or NaN.

Transformation applied:

If a respondent selected a movie → "Yes"

If missing (NaN) → "No"

This conversion:

Simplifies analysis

Enables counting and grouping

Makes visualization straightforward

5. Ranking Data Cleaning and Validation

The movie ranking columns originally contained:

Strings

Missing values

Inconsistent data types

Steps taken:

Converted ranking columns to numeric values using pd.to_numeric

Invalid values were coerced to NaN

Verified that rankings only contain values from 1 to 6

This ensures rankings can be safely used for statistical analysis.

6. Demographic Categorization
Age Categories

Original age ranges were grouped into clearer demographic categories:

Original	Category
18–29	Young Adult
30–44	Adult
45–60	Middle-Aged
> 60	Senior
Household Income Categories

Income ranges were grouped into income levels:

Original	Category
$0–$24,999	Low Income
$25,000–$49,999	Lower-Middle Income
$50,000–$99,999	Middle Income
$100,000–$149,999	Upper-Middle Income
$150,000+	High Income

These categories improve readability and allow higher-level demographic analysis.

7. Column Removal

The column “Which character shot first?” was removed as it was not relevant to the analysis goals.

8. Exporting Cleaned Data

The final cleaned dataset was exported as:

star_wars_survey_cleaned.csv


This file is:

Fully cleaned

Consistently formatted

Ready for analysis or visualization

Tools & Libraries Used

Python

pandas

Output

star_wars_survey_cleaned.csv: Cleaned and structured dataset ready for analysis

Next Steps

Possible next steps using the cleaned data:

Analyze movie popularity by demographic

Compare rankings across age or income groups

Visualize fan familiarity with characters

Perform statistical tests on ranking preferences