**Apple iPhones are among the top-selling smartphones worldwide. There is huge competition among smartphone brands in India, where you can get the latest technology in a smartphone at half the price of an iPhone. Still, there are high sales of iPhones in India.**

# iPhone Sales Analysis using Python
For the iPhone sales analysis task, I have collected a dataset from Kaggle containing data about the sales of iPhones in India on Flipkart.
**Now let’s import the necessary Python libraries** <p>
import numpy as np <p>
import plotly.express as px <p>
import plotly.graph_objects as go <p>
import pandas as pd <p>
**Reading of dataset** <p>
data = pd.read_csv("apple_products.csv") <p>
**Head of the dataset** <p>
data.head() <p>
**Tail of the dataset** <p>
data.tail() <p>
**Descriptive statistics of Dataset** <p>
data.describe() <p>

# iPhone Sales Analysis in India <p>
**Now I will create a new dataframe by storing all the data about the top 10 highest-rated iPhones in India on Flipkart. It will help in understanding what kind of iPhones are liked the most in India** <p>
highest_rated = data.sort_values(by=["Star Rating"], 
                                 ascending=False) <p>
highest_rated = highest_rated.head(10) <p>
highest_rated['Product Name']  <p>

**According to the above data, below are the top 5 most liked iPhones in India:** <p>

APPLE iPhone 11 Pro Max (Midnight Green, 64 GB) <p>
APPLE iPhone 11 Pro Max (Space Grey, 64 GB) <p>
APPLE iPhone 11 Pro Max (Midnight Green, 256 GB)  <p>
APPLE iPhone 11 Pro Max (Gold, 64 GB) <p>
APPLE iPhone 11 Pro Max (Gold, 256 GB) <p>

**Now let’s have a look at the number of ratings of the highest-rated iPhones on Flipkart:** <p>

iphones = highest_rated["Product Name"].value_counts() <p>
label = iphones.index <p>
counts = highest_rated["Number Of Ratings"] <p>
figure = px.bar(highest_rated, x=label, 
                y = counts,  
            title="Number of Ratings of Highest Rated iPhones") <p>
figure.show() <p>

**According to the above bar graph, APPLE iPhone 8 Plus (Gold, 64 GB) has the most ratings on Flipkart. Now let’s have a look at the number of reviews of the highest-rated iPhones on Flipkart:** <p>

iphones = highest_rated["Product Name"].value_counts() <p>
label = iphones.index  <p>
counts = highest_rated["Number Of Reviews"]  <p>
figure = px.bar(highest_rated, x=label, 
                y = counts, 
            title="Number of Reviews of Highest Rated iPhones") <p>
figure.show() <p>

**APPLE iPhone 8 Plus (Gold, 64 GB) is also leading in the highest number of reviews on Flipkart among the highest-rated iPhones in India. Now let’s have a look at the relationship between the sale price of iPhones and their ratings on Flipkart:** <p>

figure = px.scatter(data_frame = data, x="Number Of Ratings",
                    y="Sale Price", size="Discount Percentage", 
                    trendline="ols", 
                    title="Relationship between Sale Price and Number of Ratings of iPhones") <p>
figure.show() <p>

**There is a negative linear relationship between the sale price of iPhones and the number of ratings. It means iPhones with lower sale prices are sold more in India. Now let’s have a look at the relationship between the discount percentage on iPhones on Flipkart and the number of ratings:** <p>

figure = px.scatter(data_frame = data, x="Number Of Ratings",
                    y="Discount Percentage", size="Sale Price", 
                    trendline="ols", 
                    title="Relationship between Discount Percentage and Number of Ratings of iPhones") <p>
figure.show() <p>
**There is a linear relationship between the discount percentage on iPhones on Flipkart and the number of ratings. It means iPhones with high discounts are sold more in India.** <p>

# Summary
**So this is how we can analyze the sales of iPhones in India using the Python programming language. Some of the takeaways from this project about the sales of iPhone in India are:**  <p>

1. APPLE iPhone 8 Plus (Gold, 64 GB) was the most appreciated iPhone in India <p>
2.iPhones with lower sale prices are sold more in India <p>
3.iPhones with high discounts are sold more in India <p>
