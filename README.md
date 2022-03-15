# DS-Salary-Predictor-
Creating a tool that estimates salaries for data science roles (MAE ~ $6K) after scraping 1000s of job descriptions from glassdoor (using selenium). 

The 3MB dataset was collected through web-scraping on python, using selenium and consists of 1000s of job descriptions for positions returned after searching for 'Data Scientist' roles on Glassdoor. For each job I extracted information on a range of relevant variables, including job title, salary estimate, location - to name a few. 

Following the collection of the data, I needed to clean the dataset so that I could use it to produce a model.
I made the following changes and created the following variables:

- Parsed numeric data out of salary
- Made columns for employer provided salary and hourly wages
- Removed rows without salary
- Parsed rating out of company text
- Made a new column for company state
- Added a column for if the job was at the company’s headquarters
- Transformed founded date into age of company
- Made columns for if different skills were listed in the job description:
  Python
  R
  Excel
  AWS
  Spark
- Column for simplified job title and Seniority
- Column for description length

The exploratory data analysis returned some interesting findings, I was especially interested in observing the distributions of the data and teh value counts for various categorical variables. Here are a sample of highlights from the pivot tables: 

![Screenshot 2022-03-15 at 19 06 55](https://user-images.githubusercontent.com/93582626/158453030-51f7d5b1-ad2b-47a5-9228-ba4a84b099d7.png)
![Screenshot 2022-03-15 at 19 07 44](https://user-images.githubusercontent.com/93582626/158453036-204f8db8-d9e6-491c-bbee-461d3d68bd02.png)
![Screenshot 2022-03-15 at 19 08 03](https://user-images.githubusercontent.com/93582626/158453041-44eba4e4-0cc7-4a2a-a037-d5a8170a611f.png)

# Model Construction 

When constructing the model I transformed the categorical variables into dummy variables, as well as splitting the data into train and test sets with a test size of 20%. 

I tried built and compared three different models - evaluating with MAE for ease of interpretation. 
The models I used were: 
- Multiple Linear Regression - Baseline
- Lasso Regression
- Random Forest Model. 

The Random Forest Model was by far the best model - outperforming the other two approaches on the test and validation sets. 

Random Forest : MAE = 15.00
Linear Regression: MAE = 19.26
Ridge Regression: MAE = 20.77

### Acknowledgments

Inspiration for this topic came from the youtube videos of Ken Jee, and while I used original code the progression of this project followed the order that Ken Jee had set out. 
