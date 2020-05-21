# ELT Project Report

The goal of this project was to prep data using ETL methodology to facilitate the comparison of metal bands around the world and the World Happiness Report. 

### Extract/Data Utilized
The data was downloaded from Kaggle as CSV files(https://www.kaggle.com/mrpantherson/metal-by-nation) (https://www.kaggle.com/unsdsn/world-happiness?select=2017.csv). We initially chose the Metal 2017 dataset in order to create a project in which we were interested. The World Happiness data was available for many years, we chose 2017 because it coincided our other dataset. 

### Transformation
Once the 2 data files were extracted, we transformed using Pandas and Jupyter Notebook. First step was to import the dictionaries including pandas and sqlalchemy and reading the CSV files into dataframes. Next, we updated the column names in the metal_df to match columns in the happy_df in order to facilitate merging. After listing all of the unique country names from both files, we discovered some of the objects in the metal file contained multiple country names and that the names were inconsistent with the happy_df. We replaced every instance of 'United States' with 'USA' in the happy_df. In order to get rid of the second country name listed in some objects in the metal_df, we split the 'Country' column into 'C1' and 'C2' and removed the 'C2' (which consisted mainly of null values) and original 'Country' columns, and renamed 'C1' to 'Country'. After a little more clean up, we merged the two dataframes into merged_df and renamed all of the columns to cleaner column names.

### Load 
All three dataframes were imported into a postgreSQL database using pgAdmin. We chose to include the transformed source data in order for users to create more specific queries, if needed, and all databases are related based on 'Country'.

### Outliers
While cleaning the data, we found that some bands had two countries of origin so we removed the second listed country and only considered the first.

### Next Steps
Given infinite time and infinite resources, we would like to be the ones analyzing the data instead of doing the grunt work. Additional analysis could include Happines Rank vs Number of Metal Bands associated with each country, Trust/Corruption Factor or Dystopian Index compared with band data, or further research into political/societal events around the time the bands formed or uncoupled we could find the specific event that motivated the band to form or break up.