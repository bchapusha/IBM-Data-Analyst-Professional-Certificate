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

For the analysis we will use Python with a database instance from SQL Server, which will allow us to query data using SQL through Python.

#### ⚪ Answering Questions About The Data

##### 1. Find the total number of crimes recorded in the CRIME table.

<img src="images/question-1.jpg" width="500">

##### 2. List community areas with per capita income less than 11000.

<img src="images/question-2.jpg" width="500">

##### 3. List all case numbers for crimes involving minors?

<img src="images/question-3.jpg" width="500">

##### 4. List all kidnapping crimes involving a child?(children are not considered minors for the purposes of crime analysis)

<img src="images/question-4.jpg" width="500">

##### 5. What kind of crimes were recorded at schools?

<img src="images/question-5.jpg" width="500">

##### 6. List the average safety score for all types of schools.

<img src="images/question-6.jpg" width="500">

##### 7. List 5 community areas with highest % of households below poverty line.

<img src="images/question-7.jpg" width="500">

##### 8. Which community area(number) is most crime prone?

<img src="images/question-8.jpg" width="500">

##### 9. Use a sub-query to find the name of the community area with highest hardship index.

<img src="images/question-9.jpg" width="500">

##### 10. Use a sub-query to determine the Community Area Name with most number of crimes?

<img src="images/question-10.jpg" width="500">

---

### 🟦 Findings
