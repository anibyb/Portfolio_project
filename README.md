# PROJECT TITLE 


## NON-TECHNICAL EXPLANATION OF YOUR PROJECT
100 words to explain what your project is about to a general audience. 

This project analyzes user behavior on a peer-to-peer clothing rental platform to understand customer patterns and improve business decisions. By examining rental history, frequency, and preferences, users are grouped into segments such as frequent renters, occasional users, and VIP customers. Techniques like clustering (K-Means) and dimensionality reduction (PCA) reveal meaningful patterns, while predictive models (Logistic Regression) identify high-value or highly engaged users. Thanks to these insights, the platform can tailor strategies for each customer group, such as personalized recommendations, targeted marketing, or inventory planning, improving customer experience, loyalty, and revenue.

## DATA
A summary of the data you’re using, remembering to include where you got it and any relevant citations. 
The project uses the Vibrent Clothes Rental Dataset, available on Kaggle. The dataset contains historical user rental activity and outfit information, including outfits.csv (details of clothing items) and user_activity_triplets.csv (records of rentals by users). These files were merged on outfit.id to create a unified dataset for analysis. Key columns include user ID, outfit ID, rental start and end dates, prices, and outfit tags.

Citation:
Borgersen, K. A., Goodwin, M., Grundetjern, M., & Sharma, J. (2024). A Dataset for Adapting Recommender Systems to the Fashion Rental Economy. 18th ACM Conference on Recommender Systems. DOI: 10.1145/3640457.3688174

## MODEL 
A summary of the model you're using and why you chose it. 

Model
This project combines unsupervised and supervised learning to segment users and predict high-value customers on a clothing rental platform, helping to better understand customer behavior and develop targeted strategies for specific segments.
K-Means Clustering was used to group users based on rental behavior (total rentals, average duration, rental frequency, recency, and tag diversity). This identifies actionable customer segments such as frequent renters, occasional users, and VIP customers. The optimal number of clusters (k=6) was determined using the Elbow method and Silhouette scores.
Principal Component Analysis (PCA) reduced feature dimensionality and removed multicollinearity, improving clustering performance and visualization.
Logistic Regression predicts high-value or highly engaged users within these segments. It was chosen for its interpretability and strong performance on structured behavioral data.

Performance:
High-Value Customer Prediction: Accuracy 99.6%, Cross-Validation Accuracy 98.4%, AUC 1.0
Key predictive features: total_rentals, tag_diversity, avg_gap_days

 Business Value:
Understand different customer behaviors and preferences
Tailor marketing campaigns and loyalty programs to specific segments
Allocate resources efficiently and optimize inventory and offers

## HYPERPARAMETER OPTIMSATION
Description of which hyperparameters you have and how you chose to optimise them. 

For user grouping (K-Means), we tested different numbers of groups and chose 6, which gave the clearest distinction between customer types.
For high-value customer prediction (Logistic Regression), we adjusted settings to make the model as accurate and stable as possible.
For simplifying the data (PCA), we kept enough information to clearly see patterns while reducing complexity.

These steps ensure the model reliably identifies meaningful customer segments and predicts high-value users.

## RESULTS
A summary of your results and what you can learn from your model 

The project successfully identified six distinct customer segments based on rental behavior:
Occasional Users - rent infrequently, moderate variety of items
Power Users - highly active, broad variety of items
Frequent Short-Term Renters - rent often but for shorter durations
Moderate Active Users - average activity, smaller group
Regular Long-Term Users - rent less frequently but for longer periods
Minimal Users- very few rentals, low engagement
Using these segments, the Logistic Regression model accurately predicted high-value customers with 99.6% accuracy. Key drivers were total rentals, diversity of items rented, and rental frequency.

Business insights:
Focus resources on high-value or high-potential users
Optimize inventory based on segment preferences
Improve engagement and retention by understanding user behavior

You can include images of plots using the code below:
![Screenshot](image.png)

![alt text](<Logistic Regression results 1-3.png>)
![alt text](<Logistic Regression Results 2-1.png>)

## (OPTIONAL: CONTACT DETAILS)
If you are planning on making your github repo public you may wish to include some contact information such as a link to your twitter or an email address. 

