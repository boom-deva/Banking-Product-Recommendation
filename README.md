# Banking ProductRecommendation
**_Co-Authors:_** [Adiwid (Boom) Devahastin Na Ayudhya](https://www.linkedin.com/in/boom-devahastin/), [Muaaz Noor](https://www.linkedin.com/in/muaazahmednoor/?originalSubdomain=pk), [Tuaha Aftab](https://www.linkedin.com/in/tuaha-aftab/?originalSubdomain=pk)

## Motivation

Consumer level data contains a plethora of information that provides insight into customer behavior. Whether these are more general macro-level demographic characteristics or micro-level transaction data, the wide spectrum of existing features can easily be used to engineer new features either through brute force EDA, or more creative unsupervised learning algorithms such as clustering into interpretable personas that may themselves be used as categorical features in a supervised model. This is critical insight for marketing data scientists and product managers to recommend the appropriate strategy to target potential customers.

## Project Plan

(a)	Aim of Project: What We Intend to Study
(b)	Ultimate Goal
(c)	Potential Models Under Consideration

Here we have consumer-level banking data for a simulation of retail banking customers from Santander Bank in Spain. The dataset has over 40 features/columns that contain varying information from numeric features (e.g. age, customer tenure, gross income, etc.), multi-class categorical features (e.g. geographical origin, employment status) that will need to be one-hot encoded, and many dummy variables representing engagement with the bank’s various products.

While the original competition was far more complex in that it attempted to predict which products each and every product a customer would engage in at a specified future date (and evaluated as such using Mean Average Precision @ 7), this would be far too wide a scope for our < 1 month project. Furthermore, such an exercise may also be redundant in that it extends a base case binary classification model for 1 such banking product to the rest of them. 

To that end, we are adjusting the scope of the project by selecting 1 of the 24 banking products (from columns #25 - #48) to set as our target variable (y) and keeping the remaining products as features. The target product we have chosen is whether a user will open a Securities account. The justification is that we tried to avoid overly common features such as Savings and Checking account, which almost everyone should have as their first account with a commercial bank. At the same time, we also tried to avoid ones that were clearly more likely for a particular age group such as Mortgages because anticipating this will be highly concentrated in higher age ranges. Securities makes an interesting case since there’s a business justification behind it: retail banks such as Chase Bank or Bank of America are constantly trying to get their customers to branch out to become customers in their wealth management arm (i.e. JPM Private Bank or Merrill Lynch Wealth Management respectively).

In terms of models, we seek to first use k-Means Clustering and Hierarchical Clustering to examine if there are clusters of customers that represent a certain profile/persona (e.g. risk-averse, high liquidity, etc.) that can be used as meaningful new features in the model. Hence or otherwise, the main part of our model will then be a supervised learning problem, in particular a binary classification, via Logistic Regression, Decision Tree Classifiers, Random Forest Classifiers, and XGBoosted Tree Classifiers to predict the probability of opening a securities account. 

Extension: Time-permitting, we also seek to extend this model to build a recommender system based on a multi-classification problem where we estimate the probability of engaging with a certain product. This, however, will limit us to the tree-based models and feed-forward neural networks as classifiers.

## Caveats

The data is by no means clean and has more binary features than numeric features, which is anticipated to make parametric classifiers unwieldy to use. Examining the lifecycle of customers across the time series given will also be a very difficult manual task, which may or may not yield useful results. The narrow timeframe of just 18 months also prevents any examination of seasonality in customer behavior as only 1.5 year of data is available. There is some possible seasonality we could do with half the year that’s repeated, but otherwise limited resources on that front.
