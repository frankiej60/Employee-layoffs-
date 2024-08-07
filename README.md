# Data cleaning in MYSQL

### Project overview

The data cleaning project aims to make the raw data more useful when analysed and visualized. 


### Data source 

Employee layoffs: The primary data used for this analysis is the layoffs.data_csv file, containing detailed information about layoffs made by companies. 

### Tools

- MYSQL data cleaning and analysis
    - [Download here](https://MYSQL.com)


### Data cleaning
The following task were carried out in the data preparation phase:
- Created schema and loaded csv file
- Removed duplicates
- Standardized the data
- Reviewed nulls and blanks
- Removed columns from the duplicate dataset

  ### Codes worked with
  ---
    SQL
  
select * from lay_offs;

create table layoffs_stages
like layoffs;

select * from layoffs_stages;

insert layoffs_stages
select * 
from layoffs;

select *,
row_number () over (partition by company, location, industry, total_laid_off, 
percentage_laid_off, total_laid_off, 'date', stage, country, funds_raised_millions) as row_numz
from  layoffs_stages;

with dup_cte as (
select *,
row_number () over (partition by company, location, industry, total_laid_off, 
percentage_laid_off, total_laid_off, 'date', stage, country, funds_raised_millions) as row_numz
from  layoffs_stages)
select * from dup_cte
where row_numz > 1; 

---
