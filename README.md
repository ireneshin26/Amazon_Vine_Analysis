# **Amazon_Vine_Analysis**

## **Overview**
We are tasked with analyzing Amazon reviews written by members of the paid Amazon Vine program. 

In this project, we accessed the following dataset of reviews of Video Games: 
We then used PySpark to perform the ETL process to extract and transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. Then we used Pandas to determine if there is any bias towards favorable reviews from Vine members in the selected dataset. 

## **Data Source**
From the Amazon Review Datasets: https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt we chose the Video Games review dataset: https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Video_Games_v1_00.tsv.gz

## **Deliverable 1: Perform ETL on Amazon Product Reviews**
Using Amazon_Reviews_ETL.ipynb, we extracted the Video Games reviews dataset to the following tables: customers_df, products_df, review_id_df, and vine_df. After connecting to the AWS RDS instance, each of these DataFrames are written to the existing tables in pgAdmin. 

## **Deliverable 2: Determine Bias of Vine Reviews**

### **Overview** 
We used Pandas to determine if there is any bias towards favorable reviews from Vine members in the Vine_Table dataset. 

We filtered to the following:

* DataFrame is filtered to retrieve all the rows where the total_votes count is equal to or greater than 20 to pick reviews that are more likely to be helpful and to avoid having division by zero errors later on.

* Filter the new DataFrame or table created in Step 1 and create a new DataFrame or table to retrieve all the rows where the number of helpful_votes divided by total_votes is equal to or greater than 50%.

* Filter the DataFrame or table created in Step 2, and create a new DataFrame or table that retrieves all the rows where a review was written as part of the Vine program (paid)

* Filter the DataFrame or table created in Step 2, and create a new DataFrame or table that retrieves all the rows where a review was not part of the Vine program (unpaid)

### **Results** 
Vine Program:
* Total Number of Reviews: 94
* Number of 5 Star Reviews: 48
* % of 5 Star Reviews: 51.06%

Non-Vine Program:
* Total Number of Reviews: 40471
* Number of 5 Star Reviews: 15663
* % of 5 Star Reviews: 38.70%

### **Summary** 
Based on the results of the bias analysis, it can be seen that the Video Game reviews in the Vine Program had a 51.06% 5 star review rate compared to that of the Non Vine Program at 38.70%. This indicates that there is a positive bias towards the reviews in the Vine program. 

However, it can be seen that the number of Vine reviews is a very small sample size of the total review size so the positive bias of the Vine reviews would not be enough to affect the total ratings available on Amazon. 

#### **Recommendation for Further Analysis**
The dataset that we used included reviews across a wide range of products like consoles, controllers, hardware, and video games. It would be helpful if we narrow down the results to a specific product line and focus on the Vine Reviews in that line.
