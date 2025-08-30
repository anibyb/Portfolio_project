# Datasheet Template

As far as you can, complete the model datasheet. If you have got the data from the internet, you may not have all the information you need, but make sure you include all the information you do have. 

## Motivation

- For what purpose was the dataset created? This dataset was created to empower research in Fashion Rental Recommender Systems
- Who created the dataset (e.g., which team, research group) and on behalf of which entity (e.g., company, institution, organization)? Who funded the creation of the dataset?  Created by: University of Agder research team (e.g., Borgersen, Goodwin, Grundetjern, Sharma). In collaboration with Vibrent (formerly known as Fjong), a Norwegian fashion rental company. It is not explicitly stated who funded the creation of the dataset, however, we can assume most likely it was funded by the university or Vibrent.

 
## Composition

- What do the instances that comprise the dataset represent (e.g., documents, photos, people, countries)?  
The instances in the Vibrent Clothes Rental Dataset represent individual rental transactions that happened on Vibrent’s (formerly Fjong) clothing rental platform.
Each row in the dataset corresponds to one rental event, and includes: 1. User information (anonymized customer ID), 2.Outfit information (outfit ID, tags e.g., "Summer," "Dress," brand, size) 3.Rental period (start and end dates of the rental) 4.Rental behavior (duration of rental, frequency, categories rented)
So, the dataset doesn't directly represent people or clothes themselves - instead, it captures the interaction (a rental transaction) between a customer and an outfit.
- How many instances of each type are there? 
 The dataset contains four main types of instances: 1. Transactions (rental events; approximately 77,100 events), 2. Users (approximately 7,400 anonymised users in the dataset), 3. Outfits (approximately 15,600 unique outfits), 4. Images ( there are 50,100 photos associated with the outfits)
- Is there any missing data?
Yes, there are 1160 missing values (around 7%) in the retailPrice column associated with the outfits.csv dataframe. 
- Does the dataset contain data that might be considered confidential (e.g., data that is protected by legal privilege or by    doctor–patient confidentiality, data that includes the content of individuals’ non-public communications)?
No, the dataset does not contain any confidential data.
## Collection process

- How was the data acquired? Data was collected in collaboration with the Vibrent company.
- If the data is a sample of a larger subset, what was the sampling strategy? N/a
- Over what time frame was the data collected? 03.01.2016 - 09.06.2024

## Preprocessing/cleaning/labelling

- Was any preprocessing/cleaning/labeling of the data done (e.g., discretization or bucketing, tokenization, part-of-speech tagging, SIFT feature extraction, removal of instances, processing of missing values)? If so, please provide a description. If not, you may skip the remaining questions in this section. 
  - The Vibrent Clothes Rental Dataset was released in a preprocessed form. User IDs and outfit IDs were anonymized, outfit images were linked to metadata, and zero-shot image embeddings were precomputed. Some missing values were removed or standardized by the dataset authors. Outfit attributes such as tags and categories were provided as labeled metadata.
- Was the “raw” data saved in addition to the preprocessed/cleaned/labeled data (e.g., to support unanticipated future uses)? 
  - No, the raw data was not saved.
 
## Uses

- What other tasks could the dataset be used for? this data can be used for: 1. user personas and segmentation; 2. popularity of clothing categories; 3. customer retention and churn; 4. recommender systems for fashion rentals.
- Is there anything about the composition of the dataset or the way it was collected and preprocessed/cleaned/labeled that might impact future uses? For example, is there anything that a dataset consumer might need to know to avoid uses that could result in unfair treatment of individuals or groups (e.g., stereotyping, quality of service issues) or other risks or harms (e.g., legal risks, financial harms)? If so, please provide a description. Is there anything a dataset consumer could do to mitigate these risks or harms? 
 - The dataset is not balanced, and it is not clear if the data is representative of the population. The dataset is anonymized and partially preprocessed, which introduces both strengths and limitations. Since user demographic information is removed, fairness audits across age, gender, or socioeconomic groups cannot be performed. Outfit tags and categories may reflect subjective or culturally specific labels, which could reinforce stereotypes if applied uncritically. Furthermore, because the dataset is synthetic and created for research purposes, it may not fully represent real-world rental patterns.
A dataset consumer should be cautious about applying findings directly in production without validation against business data. To mitigate risks, one can (1) treat results as exploratory, (2) validate segmentation on a representative sample of real users, and (3) avoid making demographic assumptions from the metadata.
- Are there tasks for which the dataset should not be used? If so, please provide a description.
  - High-stakes applications, such as tasks involving financial risk or legal decisions. Predicting or inferring sensitive personal attributes (such as gender, age, income, or race) should also be avoided, as it does not contain demographic information and was not designed for profiling individuals. Since the dataset is synthetic and illustrative, it is not appropriate for direct commercial forecasting (e.g., inventory planning, pricing optimization) without validation on real-world business data.

## Distribution

- How has the dataset already been distributed? Publicly distributed via Keggle with open access.
- Is it subject to any copyright or other intellectual property (IP) license, and/or under applicable terms of use (ToU)?  The Vibrent Clothes Rental Dataset is distributed under a license that allows users to freely adapt and share the dataset, provided that proper attribution is given. The recommended citation is the accompanying paper:
Borgersen, K.A.K., Goodwin, M., Grundetjern, M., & Sharma, J. (2024). A Dataset for Adapting Recommender Systems to the Fashion Rental Economy. In 18th ACM Conference on Recommender Systems (RecSys 2024), Bari, Italy. ACM. DOI: 10.1145/3640457.3688174. 
Users are free to adapt, modify, and redistribute the dataset for educational, research, or development purposes.
Proper attribution must always be provided.

## Maintenance

- Who maintains the dataset?
The dataset is maintained by karl.audun.borgersen@uia.no

