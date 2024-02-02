# Crowdfunding_ETL

This project takes the crowd funding data provided in excel files through **Extract Transformation and Load (ETL)** process and makes it avaialble in a Postgres relational database for further usage. 

## Datasets

The input dataset is provided in 2 excel files - **crowdfunding.xlsx & contacts.xlsx.**

### Extract

The data is extracted from excel file to a Pandas DataFrame.
The category and sub-category information from crowdfunding.xlsx is extracted to **Category and Sub-category DataFrames** respectievely.
The rest of the information from crowdfunding.xlsx is extracted to **Campaign DataFrame**.
The contact information is extracted to **Contact DataFrame** 


### Transformation

**Category** - The unique values of category data loaded into the Category DataFrame is given a unique identifier for each value. The data is then saved to a csv file. 

**Sub-Category** - The unique values of sub-category data loaded into the Sub-Category DataFrame is given a unique identifier for each value. This data is then saved to a csv file.

**Campaign** - 
  * Column Rename: 'blurb', 'launched_at' and 'deadline' columnns of Campaign DataFrame are renamed to 'description', 'launched_date' and 'end_date' respectively.
  * Change Data Types:
    - 'goal' and 'pledged' columns are converted to 'float' data type using Pandas 'to_numeric' method.
    - 'launched_date' and 'end_date' columns are converted from time since epoch to datatime using Pandas to_datetime method and then converted to 'YYYY-MM-DD' format using datetime strftime() method
  * Merge DataFrames - 'Campaign' DataFrame is merged with 'Category' and 'SubCategory' DataFrame on 'category' and 'subcategory' columns respectievely to add 'category_id' and 'subcategory-id' to the 'Campaign' DataFrame
  * Drop unwanted columns from the DataFrame
  * Save the data to a csv file

### Load
  * ER Diagram - 


