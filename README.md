# Introduction
Our goal: Predict the star ratings of restaurants
How? 
Analyze Yelp’s dataset that contains customer reviews, location, pricing, and business rating
Why? Who is this useful for?
Consumer sentiment is often hard to predict without the use of mathematical models/ML.
It can help stakeholders and business owners on what to take into consideration when striving for higher ratings for their businesses
It can help business clients aspects of businesses to take into account when thinking about choosing their services, investing in them, etc

## Raw Data
We used the Yelp Open Dataset, which contained 4 compressed GB of business, review, and user data like hours of availability, parking, and ambience. 
1.2 million business attributes
150,346 businesses
6,990,280 reviews
200,100 pictures
11 metropolitan areas

## Methods
#### Text Analysis
Visualize Categories column
Helpful for determining which categories might be helpful to include for model features
Looked into each cluster to see which may be useful categories
Light Blue: Types of Food
Red cluster: Latin food
Pre-processed data into an adjective data subset
Tokenized the list of reviews and tagged them by their adjectives
Skip Grams model to find adjective-noun pair similarity
Useful in determining sentiment of particular items in the reviews to better inform business owners of what to improve
Such adjectives like “nice” would be paired with “food” and “atmosphere”

#### Sentiment Analysis
Processed text data from every individual review from the California Yelp Dataset
How can we understand what makes businesses receive high and low reviews and star ratings?
WordCloud
Identified trends in positive and negative reviews
Negative reviews focused on the bad aspects (food, wait time, etc)
Positive reviews had positive adjectives and focused on the setting (restaurant and the staff)
Sentiment Analysis Model
VADER (Valence Aware Dictionary for Sentiment Reasoning)


#### Neural Networks/ Feature Selection
Emulated Lab 4 (MLPClassifier, etc)
Due to the large amount of available features, our approach to selecting our features was as follows:
EDA
Personal Experience
Checking improvement in model performance
Grid Searches
Observing what features 
most businesses had, reducing
the number of incomplete
entries when training models


## Findings  and Results
WLLN tells us that user tends to have an average score around slightly under 4
Our finding also compliments the results of our previous page, as the user has more experience as an elite member they start to average out their scores to around 4
We can see that there is a slight correlation between the number of friends you have and your average score. This can be because the number of friends can be representative of the length of time you have been reviewing and as we mentioned before people will average out to 4 after a while
We see how on average if the review is useful, cool or funny they also tend to give a positive review
We see how for funny, if the review is seen as very funny it might not necessarily mean that the review is positive, while the other categories all have a slight positive correlation


## Linear Regression Model
Our first approach to finding an accurate way to predict ratings
High amount of features meant that model was 
at risk of overfitting
Yielded less accurate results, needed more complex methods
Multicollinearity possible
Amongst wide number of
Features
Cross validation with 5 folds only helped score slightly
Mean squared error of .42

## Random Forest Model
This method worked the best for our prediction in the Titanic Kaggle dataset, so we wanted to utilize it for this project as well and see how it fared
The mse of the predictions using the random forest model was about 0.0611; a really good score!
Every prediction would be about .25 off, or a 0.5 score mistake for every other prediction (as ratings only go by 0.5)
Allowed us to extract feature importances
Found more success when making prediction variable binary


## Neural Network Model
As a complex dataset, we also wanted to emulate what we learned in Lab 4 and see if we could beat our previous accuracies in lab.
Dataset was large enough to make use
of neural network models, along with complex predictions (star ratings)
Neural Networks excel in utilizing less structured data, such as text from reviews
Utilized GridSearchCV and RandomizedSearchCV
Found a test accuracy of ~88%, much higher than our Lab 4 accuracies
Ref: The best hyperparameters were hidden_layer_sizes=(200,), activation='logistic', solver='adam', learning_rate_init = 0.1, alpha=0.001, learning_rate= 'adaptive', random_state=42, early_stopping = True, max_iter=200, batch_size=64


# Conclusion
Our findings indicate that there are measurable patterns between users and business reviews.
We also recognized some shortcomings that we believe should be addressed in future research.
Yelp’s Biases
Fake reviews might artificially boost the ratings of restaurants
Yelp and their ratings are not representative of all customers
Badly rated restaurants might have improved, but customers might not try a restaurant a second time to reflect changes in a restaurant
Location
Due to the size of the dataset, we only were able to work with reviews from California, especially Santa Barbara. Seeing if our work can be replicated in other settings would be interesting work.
Modeling
Utilizing different methods and hyperparameters could further optimize our model.

