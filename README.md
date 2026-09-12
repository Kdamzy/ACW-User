### ACW User Data Processing and Visualisation
#### Project Overview
This project focuses on processing, cleaning, restructuring and visualising the ACW user dataset using Python.
The original data was provided in CSV format and contains different information about customers such as their personal details, employment information, salary, pension, commuting distance, vehicle details, credit card information and address.
The project contains 1,000 customer records.

#### Tools and Libraries Used
* Python
* CSV – to read the original CSV file
* JSON – to create and read JSON files
* Pandas – for data analysis and cleaning
* Seaborn – for data visualisation
* Jupyter Notebook – to write and run the analysis

#### Data Processing

1. Reading the Dataset
I started by reading the acw_user_data.csv file using csv.DictReader().
Each customer record was stored as a dictionary inside a list. I also included exception handling so that errors such as a missing file can be reported. A total of 1,000 records were successfully loaded.

2. Converting the Flat Data into Nested Structures
The original CSV file contains all customer information in a flat structure.
I created separate functions to organise the following information into nested dictionaries:
* Vehicle
* Credit Card
* Address
I also created functions to convert values into the correct data types

3. Checking the Dependants Column
I checked the Dependants column for missing or empty values.
A total of 19 records were found with missing dependant information.
The affected row indexes were recorded so the problem could be identified before further analysis.

4. Creating the Processed JSON File
After restructuring the data, I saved all processed customer records into processed.json file
I then loaded the file back into Python and compared it with the original processed list to make sure that the data was saved correctly.
The comparison returned True, confirming that the saved JSON data matched the processed records.

5. Separating Retired and Employed Customers
I separated the customer records into two different groups.
Customers with a Retired value of True were saved into retired.json file
Customers who were not retired and had a valid employer name were saved into employed.json file
The result was:
* Retired customers: 246
* Employed customers: 754

6. Checking Credit Card Duration
I created a function to calculate the duration between each customer's credit card start date and expiry date.
The dates were converted into months so that the total duration could be calculated.
Any credit card with a duration greater than 10 years was flagged.
A total of 252 customer records were identified and saved into remove_ccard.json file

7. Creating the Salary-Commute Attribute

I created a new customer attribute called Salary-Commute
This represents the customer's yearly salary in relation to the distance they commute to work.
For customers travelling more than 1 km, the value was calculated as:
Salary-Commute = Yearly Salary / Distance Commuted to Work
For customers travelling 1 km or less, their yearly salary was used as the Salary-Commute value.
The updated customer records were then sorted in ascending order and saved into commute.json file

#### Data Analysis and Visualisation

After completing the data processing section, I used Pandas and Seaborn to carry out some basic analysis and visualisation using the original CSV file.

1. Univariate Analysis
I created plots to examine individual customer attributes.

2. Age Distribution
The age range was divided using a bin width of 5.
A total of 15 bins were used to display the age distribution.

3. Dependants Distribution
The Dependants column was converted to numeric values using Pandas.
Invalid or missing values were converted to missing values and then replaced with 0.
A count plot was created to show the distribution of the number of dependants.

4. Age by Marital Status
I created a stacked histogram to show the age distribution based on marital status.

5. Multivariate Analysis
I also created scatter plots to examine the relationship between different customer attributes.

6. Commute Distance Against Salary
This plot was used to examine the relationship between the distance travelled to work and yearly salary.

7. Age Against Salary
This plot shows the relationship between customer age and yearly salary.

8. Age Against Salary Conditioned by Dependants
I created another scatter plot to compare age and salary while using the number of dependants as an additional variable.


#### How to Run the Project
* Clone or download this repository.
* Make sure acw_user_data.csv is in the same project folder as the notebook.
* Install the required external libraries:
* pip install pandas seaborn
* Open the Jupyter Notebook.
* Run the notebook cells from the beginning to the end.
* The JSON output files and plots will be created while the notebook is running.