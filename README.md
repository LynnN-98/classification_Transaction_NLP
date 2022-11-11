# Determine Transaction Categories Using Machine Learning and NLP

It is no surprise that financial companies need to help their customers organize their finances. Customers want to know what they spend their money on to keep balances in check. By categorizing transactions and building better customer engagement tools, Wells Fargo can help customers identify frequent purchases and subscriptions, sort income and activity liability with higher accuracy, and reduce credit risks. 

Transaction categorization is the ability to recognize the purpose of a transaction based on its description. For long, this process was done manually but now technology can do it efficiently.

In the data challenge sponsored by Wells Fargo Bank, I built a project to predict transaction categories based on the description text data of the transactions. Finally, the F1 score of the best model on the training test was improved to 93.905%.

The 10 categories to be predicted are as follows:

• Communication Services 
• Education 
• Entertainment
• Finance 
• Health and Community Service 
• Property and Business Services 
• Retail Trade 
• Services to Transport 
• Trade, Professional and Personal Services
• Travel 

The following model combinations were compared to select the best performing one:

TF-IDF +  Naive Bayes: accuracy=0.39

TF-IDF + XGBoost: f1-score=0.93905

TF-IDF + MLP: f1-score=0.49705

BERT + MLP: f1-score=0.57545

In the first three methods, I applied TF-IDF to vectorize the text features (trans_desc, default_brand, default_location, and coalesced_brand) and get a 39994x70 sparse matrix. After combining the sparse matrix with the remaining features, the final feature set was fed into the Naive Bayes, XGBoost, and MLP classifiers to get the classification results. The prediction results of the 2nd (best) model are saved in the file Test Data Set New Category.xlsx

To compare with them, I encoded the text features with the BERT uncase base and used the output of the BERT model pooling layer as the encoding result. Considering the possible model overfitting in the 2nd method, the prediction results of the 4th model are saved in file prediction.xlsx

Implementation Details: 

![roadmap](https://user-images.githubusercontent.com/63036112/201251102-5b2300f2-ed2b-43a1-b657-36e6869ff04c.png)

For the exploratory data analysis, I dropped some features with high missing rates, high skewness, or duplicate information. 6 rows were dropped considering the missing value and their weight in the overall dataset. I also cleaned the trans_desc column by Regex to remove the meaningless text. For feature selection, I found the features with a high correlation with the target variable by generating bar plots.
