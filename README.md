# SQL-data-cleaning
## Introduction
This is an educational project on data cleaning and preparation using SQL. The original database in CSV format is located in the file club_member_info.csv. Here, we will explore the steps that need to be applied to obtain a cleansed version of the dataset.
## Original-formatted Data Analysis
Let's inspect the initial rows to analyze the data in its original formats

    SELECT * 
    FROM club_member_info 
    LIMIT 10

|full_name|age|martial_status|email|phone|full_address|job_title|membership_date|
|---------|---|--------------|-----|-----|------------|---------|---------------|
|addie lush|40|married|alush0@shutterfly.com|254-389-8708|3226 Eastlawn Pass,Temple,Texas|Assistant Professor|7/31/2013|
|      ROCK CRADICK|46|married|rcradick1@newsvine.com|910-566-2007|4 Harbort Avenue,Fayetteville,North Carolina|Programmer III|5/27/2018|
|Sydel Sharvell|46|divorced|ssharvell2@amazon.co.jp|702-187-8715|4 School Place,Las Vegas,Nevada|Budget/Accounting Analyst I|10/6/2017|
|Constantin de la cruz|35||co3@bloglines.com|402-688-7162|6 Monument Crossing,Omaha,Nebraska|Desktop Support Technician|10/20/2015|
|  Gaylor Redhole|38|married|gredhole4@japanpost.jp|917-394-6001|88 Cherokee Pass,New York City,New York|Legal Assistant|5/29/2019|
|Wanda del mar       |44|single|wkunzel5@slideshare.net|937-467-6942|10864 Buhler Plaza,Hamilton,Ohio|Human Resources Assistant IV|3/24/2015|
|Joann Kenealy|41|married|jkenealy6@bloomberg.com|513-726-9885|733 Hagan Parkway,Cincinnati,Ohio|Accountant IV|4/17/2013|
|   Joete Cudiff|51|divorced|jcudiff7@ycombinator.com|616-617-0965|975 Dwight Plaza,Grand Rapids,Michigan|Research Nurse|11/16/2014|
|mendie alexandrescu|46|single|malexandrescu8@state.gov|504-918-4753|34 Delladonna Terrace,New Orleans,Louisiana|Systems Administrator III|3/12/1921|
| fey kloss|52|married|fkloss9@godaddy.com|808-177-0318|8976 Jackson Park,Honolulu,Hawaii|Chemical Engineer|11/5/2014|

## Get Started
### PART 1: Copy the table
Let's generate a copied table so that we can manipulate and reconstruct the data without modifying the original data

    CREATE TABLE club_member_info_cleaned (
	full_name VARCHAR(50),
	age INTEGER,
	martial_status VARCHAR(50),
	email VARCHAR(50),
	phone VARCHAR(50),
	full_address VARCHAR(50),
	job_title VARCHAR(50),
	membership_date VARCHAR(50)
 );


Then copy all the values from the original table to the copied table

INSERT INTO club_member_info_cleaned
SELECT * FROM club_member_info;    

### PART 2: Clean the data
Regarding the copied database, there are several issues that we need to modify including
- Inconsistent letter case
- Age out of realistic range
- Leading and trailing whitespaces
#### Inconsistent letter case
To remain the consistency, we set a specific rule for the data. In this case, I would like to transfer all the letter in full_name column to UPPERCASE. Don't forget to update the table to save the action.

UPDATE club_member_info_cleaned 
SET full_name = UPPER(full_name)

#### Age out of realistic range
There are some cells contain whose age is impossible like 352 years old. Thus, to reduce the error during data analysis, I would like to remove all the customers info whose age is unreal. Giving the realistic range from 18 to 100 years old. 

DELETE from club_member_info_cleaned 
WHERE age NOT BETWEEN 18 AND 100

#### Leading and trailing whitespaces
To remove both leading and trailing whitespaces, trimming is an ideal statement. Don't forget to update the table to save the action

UPDATE club_member_info_cleaned 
SET full_name = TRIM(full_name)





