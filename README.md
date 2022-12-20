# Amazon_Vine_Analysis

# Overview of the analysis:
The purpose of this project is to analyze Amazon Vine reviews written by members of the paid Amazon Vine program and share the findings with SellBy stakeholders.
The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews of their products. Companies like SellBy pay Amazon a small fee and provide products to Amazon Vine members, who are required to post a review.
In this project, we analyze the toy reviews available through the link "https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Toys_v1_00.tsv.gz".
We use PySpark to run the ETL process to extract and transform the dataset, connect to an AWS RDS instance, and load the transformed data into pgAdmin. We then use Pandas to determine if there is any bias towards favorable Vine member ratings in the dataset.
Below is a summary of the analysis.

# Results:
Seeking to analyze whether having a paid Vine review makes a difference in the percentage of 5-star reviews, we used Pandas to determine whether this is biased against reviews written as part of the Vine program.
First, we filter the data to retrieve all rows where the Total Votes is 20 or greater to choose reviews that are most likely to be useful and to avoid divide-by-zero errors later. After that, we selected all lines where the number of useful_votes divided by total_votes is equal to or greater than 50%.
With the new database ready, we arrived at the result of the summary table below, where we found that:

 - Out of a total of 63294 reviews, we have 1266 amount of paid reviews and 62028 unpaid reviews.
 - Selecting only the 5 star reviews, we arrive at a total of 30414, with 432 Vine reviews and 29982 non-Vine reviews.
 - Finally, we looked at the percentage of Vine reviews that were 5 stars out of the total helpful reviews. Vine reviews were at 0.68% while the percentage of non-Vine reviews were at 47.4%.

# Summary:
Analyzing the results above, based on the data made available for toys for the reviews written as part of the Vine program, we can conclude that being part of this program does not present a positive bias for the 5 star rating.
As a suggestion for analysis to better support these results would be to check the 5 star ratings based on the helpful_votes, as we could check whether being part of the Vine program has more helpful votes in the 5 star ratings than non-participants in this program.

The entire ETL transformation is found in the Amazon_Reviews_ETL.ipynb file.
Analysis of the biases of Vine reviews are in the file Vine_Review_Analysis.ipynb with the code commented out.
The vine_table.csv file contains the data used in this analysis.
