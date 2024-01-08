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
![image](https://github.com/KalyanKumarBhogi/Comprehensive_Analysis_of_Iphone_sales_in_-india/assets/144279085/8d32f561-11aa-4205-bb28-f6df54010560)
**Head of the dataset** <p>
data.head() <p>
![image](https://github.com/KalyanKumarBhogi/Comprehensive_Analysis_of_Iphone_sales_in_-india/assets/144279085/204eb791-14f5-40aa-b66e-242a33d699a2)

**Tail of the dataset** <p>
data.tail() <p>
![image](https://github.com/KalyanKumarBhogi/Comprehensive_Analysis_of_Iphone_sales_in_-india/assets/144279085/c507e64e-b137-4e70-b8fd-bce39d112c92)

**Descriptive statistics of Dataset** <p>
data.describe() <p>
![image](https://github.com/KalyanKumarBhogi/Comprehensive_Analysis_of_Iphone_sales_in_-india/assets/144279085/91923a98-55fc-4acc-ae8f-a111b5c20f95)

Before moving forward, let’s have a quick look at whether this dataset contains any null values or not: <p>

print(data.isnull().sum()) <p>

![image](https://github.com/KalyanKumarBhogi/Comprehensive_Analysis_of_Iphone_sales_in_-india/assets/144279085/78361f30-de5b-41fb-bc52-54a821c89748)

# iPhone Sales Analysis in India <p>
**Now I will create a new dataframe by storing all the data about the top 10 highest-rated iPhones in India on Flipkart. It will help in understanding what kind of iPhones are liked the most in India** <p>
highest_rated = data.sort_values(by=["Star Rating"], 
                                 ascending=False) <p>
highest_rated = highest_rated.head(10) <p>
highest_rated['Product Name']  <p>

![image](https://github.com/KalyanKumarBhogi/Comprehensive_Analysis_of_Iphone_sales_in_-india/assets/144279085/66eeea8b-8138-4966-8405-fcdf206125c8)

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
![image](https://github.com/KalyanKumarBhogi/Comprehensive_Analysis_of_Iphone_sales_in_-india/assets/144279085/c40c27d9-6a2d-4bd8-b486-05e4319f88d0)

**According to the above bar graph, APPLE iPhone 8 Plus (Gold, 64 GB) has the most ratings on Flipkart. Now let’s have a look at the number of reviews of the highest-rated iPhones on Flipkart:** <p>

iphones = highest_rated["Product Name"].value_counts() <p>
label = iphones.index  <p>
counts = highest_rated["Number Of Reviews"]  <p>
figure = px.bar(highest_rated, x=label, 
                y = counts, 
            title="Number of Reviews of Highest Rated iPhones") <p>
figure.show() <p>
![image](https://github.com/KalyanKumarBhogi/Comprehensive_Analysis_of_Iphone_sales_in_-india/assets/144279085/82de9d03-5788-4352-a897-1fdbf5411520)


**APPLE iPhone 8 Plus (Gold, 64 GB) is also leading in the highest number of reviews on Flipkart among the highest-rated iPhones in India. Now let’s have a look at the relationship between the sale price of iPhones and their ratings on Flipkart:** <p>

figure = px.scatter(data_frame = data, x="Number Of Ratings",
                    y="Sale Price", size="Discount Percentage", 
                    trendline="ols", 
                    title="Relationship between Sale Price and Number of Ratings of iPhones") <p>
figure.show() <p>

![image](https://github.com/KalyanKumarBhogi/Comprehensive_Analysis_of_Iphone_sales_in_-india/assets/144279085/471bc19d-a62d-4f91-bd50-64f74eda7329)

**There is a negative linear relationship between the sale price of iPhones and the number of ratings. It means iPhones with lower sale prices are sold more in India. Now let’s have a look at the relationship between the discount percentage on iPhones on Flipkart and the number of ratings:** <p>

figure = px.scatter(data_frame = data, x="Number Of Ratings",
                    y="Discount Percentage", size="Sale Price", 
                    trendline="ols", 
                    title="Relationship between Discount Percentage and Number of Ratings of iPhones") <p>
figure.show() <p>
![image](https://github.com/KalyanKumarBhogi/Comprehensive_Analysis_of_Iphone_sales_in_-india/assets/144279085/555f0b0f-d23a-4b11-9377-e3a6f09764dd)

**There is a linear relationship between the discount percentage on iPhones on Flipkart and the number of ratings. It means iPhones with high discounts are sold more in India.** <p>

# Conclusion <p>
The analysis of iPhone sales in India, utilizing a dataset from Flipkart, revealed insightful patterns and preferences. The top-rated iPhones in India, such as the APPLE iPhone 8 Plus (Gold, 64 GB), garnered the highest number of ratings and reviews on Flipkart. Notably, there exists a negative linear relationship between iPhone sale prices and the number of ratings, suggesting that iPhones with lower prices are more popular. Additionally, the analysis unveiled a positive linear relationship between the discount percentage and the number of ratings, indicating that iPhones with higher discounts witness increased sales in the Indian market. These findings underscore the significance of pricing and promotional strategies in influencing iPhone sales trends in the competitive Indian smartphone market. <p>
