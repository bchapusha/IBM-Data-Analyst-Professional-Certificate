# Databases and SQL for Data Science with Python

**Course description**:

Introduction to SQL for data analysis and using SQL with Python. Building queries and working with real databases on the IBM cloud to analyze and draw data-driven conclusions.

---

## Final Project: Identify Causes That Impact the Enrollment, Safety, Health, Environment Ratings of Schools in Chicago

### 🧰 Materials

* [Completed IBM Lab Jupyter Notebook](ibm-project-notebook.ipynb)

Tools:

* [SQL Server Management Studio 19](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16)

Datasets:
* [**Chicago Census Data**](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/FinalModule_Coursera_V5/data/ChicagoCensusData.csv?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDB0201ENSkillsNetwork20127838-2021-01-01): This dataset contains a selection of six socioeconomic indicators of public health significance and a hardship index, by Chicago community area, for the years 2008 – 2012
* [**Chicago Public Schools**](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/FinalModule_Coursera_V5/data/ChicagoPublicSchools.csv?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDB0201ENSkillsNetwork20127838-2021-01-01): This dataset shows all school level performance data used to create CPS School Report Cards for the 2011-2012 school year.
* [**Chicago Crime Data**](https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DB0201EN-SkillsNetwork/labs/FinalModule_Coursera_V5/data/ChicagoCrimeData.csv?utm_medium=Exinfluencer&utm_source=Exinfluencer&utm_content=000026UJ&utm_term=10006555&utm_id=NA-SkillsNetwork-Channel-SkillsNetworkCoursesIBMDeveloperSkillsNetworkDB0201ENSkillsNetwork20127838-2021-01-01): This dataset reflects reported incidents of crime (with the exception of murders where data exists for each victim) that occurred in the City of Chicago from 2001 to present, minus the most recent seven days.

### 🟦 Introduction

For this project, you will be working on a real world dataset provided by the Chicago Data Portal. You have been hired by a non-profit organization that strives to improve educational outcomes for children and youth in the City of Chicago. Your job is to analyze the census, crime, and school data for a given neighborhood or district. You will identify causes that impact the enrollment, safety, health, environment ratings of schools.

---

### 🟦 Analysis

#### ⚪ Access SQL Databases through Python

For the analysis we will use Python with a database instance from SQL Server, which will allow us to query data using SQL through Python.

The following code load the sql module and connects to a database instance

```
%load_ext sql
%sql mssql+pyodbc://sa:****@SQLMain
```

#### ⚪ Answering Questions About The Data

##### 1. Find the total number of crimes recorded in the CRIME table.

```
%%sql

SELECT COUNT(CASE_NUMBER) AS 'Number of Recorded Crimes'
FROM CHICAGO_CRIME_DATA;
```

<img src="images/question1.jpg" width="1100">

##### 2. List community areas with per capita income less than 11000.

```
%%sql

SELECT COMMUNITY_AREA_NAME AS 'Community Areas with per capita < 11000'
FROM CENSUS_DATA
WHERE PER_CAPITA_INCOME < 11000
ORDER BY COMMUNITY_AREA_NAME;
```

<img src="images/question2.jpg" width="1100">

##### 3. List all case numbers for crimes involving minors?

```
%%sql

SELECT CASE_NUMBER 'Case Numbers Involving Minors'
FROM CHICAGO_CRIME_DATA
WHERE DESCRIPTION LIKE '%MINOR%';
```

<img src="images/question3.jpg" width="1100">

##### 4. List all kidnapping crimes involving a child?(children are not considered minors for the purposes of crime analysis)

```
%%sql

SELECT * 
FROM CHICAGO_CRIME_DATA
WHERE PRIMARY_TYPE = 'KIDNAPPING';
```

<img src="images/question4.jpg" width="1100">

##### 5. What kind of crimes were recorded at schools?

```
%%sql

SELECT DISTINCT(PRIMARY_TYPE) AS 'Crimes Recorded at Schools'
FROM CHICAGO_CRIME_DATA
WHERE LOCATION_DESCRIPTION LIKE '%SCHOOL%';
```

<img src="images/question5.jpg" width="1100">

##### 6. List the average safety score for all types of schools.

```
%%sql

SELECT Elementary_Middle_or_High_School AS 'Type of School', AVG(SAFETY_SCORE) AS 'Average Safety Score'
FROM CHICAGO_PUBLIC_SCHOOLS
GROUP BY Elementary_Middle_or_High_School;
```

<img src="images/question6.jpg" width="1100">

##### 7. List 5 community areas with highest % of households below poverty line.

```
%%sql

SELECT TOP 5 COMMUNITY_AREA_NAME AS 'Community Area', 
           CONVERT(DECIMAL(4,1), PERCENT_HOUSEHOLDS_BELOW_POVERTY) AS '% Households Below Poverty Line'
FROM CENSUS_DATA
ORDER BY PERCENT_HOUSEHOLDS_BELOW_POVERTY DESC;
```

<img src="images/question7.jpg" width="1100">

##### 8. Which community area(number) is most crime prone?

```
%%sql

SELECT TOP 1 CENSUS_DATA.COMMUNITY_AREA_NAME AS 'Community Area', 
             COUNT(CHICAGO_CRIME_DATA.COMMUNITY_AREA_NUMBER) AS 'Number of Crimes'
FROM CHICAGO_CRIME_DATA
INNER JOIN CENSUS_DATA
ON CHICAGO_CRIME_DATA.COMMUNITY_AREA_NUMBER = CENSUS_DATA.COMMUNITY_AREA_NUMBER 
GROUP BY CENSUS_DATA.COMMUNITY_AREA_NAME
ORDER BY COUNT(CHICAGO_CRIME_DATA.COMMUNITY_AREA_NUMBER) DESC;
```

<img src="images/question8.jpg" width="1100">

##### 9. Use a sub-query to find the name of the community area with highest hardship index.

```
%%sql

SELECT COMMUNITY_AREA_NAME AS 'Community Area with Highest Hardship Index'
FROM CENSUS_DATA
WHERE HARDSHIP_INDEX = (SELECT MAX(HARDSHIP_INDEX) FROM CENSUS_DATA);
```

<img src="images/question9.jpg" width="1100">

##### 10. Use a sub-query to determine the Community Area Name with most number of crimes?

```
%%sql

SELECT TOP 1 COMMUNITY_AREA_NAME AS 'Community Area with Most Crimes'
FROM CENSUS_DATA
WHERE COMMUNITY_AREA_NUMBER = (SELECT TOP 1 COMMUNITY_AREA_NUMBER 
                               FROM CHICAGO_CRIME_DATA 
                               GROUP BY COMMUNITY_AREA_NUMBER 
                               ORDER BY COUNT(COMMUNITY_AREA_NUMBER) DESC);
```

<img src="images/question10.jpg" width="1100">

---

### 🟦 Findings
