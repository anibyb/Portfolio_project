# Model Card

See the [example Google model cards](https://modelcards.withgoogle.com/model-reports) for inspiration. 

## Model Description
The initial input dataset is the Vibrent Clothes Rental dataset available on Kaggle. The project used two source files: outfit.csv and user_activity_triplets.csv. These were merged on the outfitID column, producing a combined dataframe with the following 10 columns:
customer.id
outfit.id
outfit_tags
timeCreated
retailPrice
pricePerWeek
pricePerMonth
rental_start
rental_end
rental_duration_days

From this merged dataset, several behavioral features were engineered to capture user activity patterns. These included:
total rentals per user
average rental duration
average gap between rentals
recency (days since last rental)
tag diversity (variety of outfit categories rented)
After correlation analysis and feature selection, the final inputs used in the models were:
total_rentals
avg_duration
avg_gap_days
recency_days
tag_diversity

**Output:** Describe the output(s) of your model
Output
The models were designed as binary classifiers to predict different types of user segments in the rental platform. Specifically:
High-Value Customer Classification: outputs 1 if the user is a high-value customer (top 25% by rental frequency) and 0 otherwise.
Active User Classification: outputs 1 if the user meets the selected “recent activity” threshold and 0 otherwise.
Power User Classification: intended to output 1 for power users and 0 for regular users, but this model could not be trained due to lack of class balance.
Each model also outputs a probability score (between 0 and 1) representing the likelihood of belonging to the positive class.
The best performing model was the High-Value Customer classifier, achieving:
Accuracy: 99.6%
Cross-validation accuracy: 98.4% (±0.5%)
AUC: 1.0
The final output of the deployed model is therefore:
Prediction (0 = regular customer, 1 = high-value customer)
Probability score (confidence level for the prediction)

**Model Architecture:** Describe the model architecture you’ve used

Model Architecture
The model pipeline combines unsupervised and supervised methods:
K-Means Clustering (k=6):
- Optimal number of clusters determined using the Elbow method and Silhouette score.
- Resulting clusters mapped to six behavioral segments (e.g., Occasional Users, Power Users).
Feature Correlation & Selection:
-  High correlation identified between total_rentals and tag_diversity (r = 0.87).
- To reduce redundancy, only total_rentals, avg_gap_days, and recency_days were retained.
Principal Component Analysis (PCA):
- Reduced the selected features into 2 principal components.
- Achieved 83.9% explained variance while ensuring orthogonal (uncorrelated) features.
Logistic Regression:
- Final supervised classification stage.
- Uses the PCA-transformed features as input.
- Outputs probability of belonging to the target class (e.g., high-value vs. regular customer).

## Performance

Give a summary graph or metrics of how the model performs. Remember to include how you are measuring the performance and what data you analysed it on. 

Clustering (K-Means, k=6):
- How measured: Elbow Method (inertia reduction) and Silhouette Score (cohesion vs. separation). 
Elbow method for K:![alt text](<Elbow method for K-2.png>)
Silhouette Analysis for K:![alt text](<Silhouette Analysis for K-1.png>)
Cluster Heatmap:![alt text](<Clusters - Heatmap.png>) 

Dimensionality Reduction (PCA):
- How measured: Explained variance ratio.
PCA Analysis: ![alt text](<PCA ANALYSIS.png>)
2D PCA: ![alt text](<2D PCA.png>)

Classification (Logistic Regression):
- How measured: Accuracy, Precision, Recall, F1-score, and Confusion Matrix.
- Dataset: Final engineered features (total_rentals, avg_gap_days, recency_days) transformed by PCA.

Logistic Regression Results: 
![alt text](<Logistic Regression results 1-1.png>)
![alt text](<Logistic Regression Results 2.png>)

## Limitations

Outline the limitations of your model.

Temporal Scope: Dataset only covers historical rentals up to 2024; metrics like recent rentals cannot reflect current behavior.

Feature Constraints: Some features were removed due to high correlation; user behavior may not capture seasonal trends.

Cluster Limitations: K-Means assumes spherical clusters; very small clusters may be less reliable.

Supervised Model Constraints: Logistic Regression assumes linear relationships; classes with few instances (e.g., Power Users) cannot be modeled effectively.

Potential Bias: Dataset may overrepresent certain user types or categories; predictions may not generalize to new users.

External Factors Ignored: No demographic or location data; business decisions should combine model insights with domain expertise.

## Trade-offs

Outline any trade-offs of your model, such as any circumstances where the model exhibits performance issues. 

The model balances interpretability, performance, and usability. Logistic Regression is easy to explain but may miss complex non-linear patterns. K-Means segmentation provides actionable user groups but assumes spherical clusters, which may not capture all behavioral nuances. Smaller clusters offer detailed insights but are less statistically reliable, while removing correlated features reduces multicollinearity at the cost of discarding some predictive information. Finally, the model is trained on historical data, so predictions may not fully generalize to new users or changing market trends.
