# Feature-Analysis
Analyzing variables, modeling and data cleaning to determine factors that contribute to the success rate of a movie.


**Feature Analysis of Movie Attributes :** <br />
A Movie can be classified as a successful movie or a ' hit' based on the revenue it earns for the budget put into its making. Of course, the story of the Movie plays a vital role in determining that. However, there could be hidden patterns in the movie attributes that have more influence over others in deciding whether a movie will be a hit or not. By analyzing various attributes of a movie, this project aims to achieve that.
The project consisted of Exploratory Data Analysis and Statistical Modelling of a movies database from Kaggle – "The Movies Dataset". This database consisted of attributes such as Cast, Crew, Plot keyword, Budget, Revenue, Posters, Release date, Languages, Production, Companies, Countries, IMDB votes, IMDB Ratings, and Vote average.

**The project goal is achieved by the following 3 steps.** <br />
Importing and Tidying Data.<br />
Exploratory Data Analysis.<br />
Feature Analysis.<br />

**Data Sources** <br />
The Movie Dataset.<br />
IMDB Movies dataset.<br />
IMDB Ratings dataset.<br />



**Data Tidying** <br />
* Load the "movies_dataset.csv file". <br />
* Drop/Discard irrelevant features/Variables. <br />
* “Genres” and “Production Countries” data was present in a form of {key:value} pair and needed to be split. Further, each cell was populated with multiple           {key:value} pairs, indicating that a movie has multiple genres and multiple production countries. The first step to tidy this data was to extract only the           values from the {key:value} pairs. This resulted in all genres/production countries being populated in a comma separated format. It was observed that overall,       there were 20 unique genres and 111 production countries. Hence, 20 columns for each genre and 111 columns for each country were added to the dataset. Using         the comma separated genres and countries in the first step, the 20 genre columns and 111 country columns were populated as 1 or 0. Thus, all genres and             production countries a movie were obtained as separate features. <br />
* Merge main data, ‘The Movie Dataset’ with ‘IMDB Movies Data’ and ‘IMDB Ratings Data’ to source Budget, Revenue, Release Year and Ratings of movies.
* Revenue and Budget Columns were populated with different currencies. Hence, they were converted to a single currency (USD) to bring the values on the same scale     using the ‘priceR’ package. This package uses an API that sources exchange rates against USD of the current day from the world bank.
* Y-Variable/Target variable: The Y-variable/Target variable of the model was created from the data. The ratio of the revenue and the budget was used to               categorize a movie as ‘Hit’ or ‘Not Hit’. The value of the ratio greater than 1 was categorized as ‘Hit’ and less than 1 was categorized as ‘Not Hit’.



**Exploratory Data Analysis.** <br />

* Distribution of the Response Variable:	<br />
	* The response variable is calculated based on the ratio of already existing variables named revenue and budget. If the ratio of the revenue to budget comes out to be greater than 1, meaning profits were generated, it is marked as a hit movie, or is  not a hit otherwise. The distribution of the response variable can be seen from figure 1. As expected, the number of movies decreases with increase in Revenue to Budget ratio. Also, 51.4% of movies have Revenue to Budget ratio greater than 1. Thus 51.4% of the movies are categorized as ‘Hit’ and remaining as ‘Non-Hit’. The Y-variable thus has a balanced class.
<p align="center"> <img width="450" alt="Picture1" src="https://user-images.githubusercontent.com/93501171/146658667-93c4c48e-9afc-4f71-8073-31b91fa20991.png"> </p> 


**MODELLING:**

* Modelling is the methodology of trying to make a Machine Learning model to take in our dataset and predict a target variable. It also includes minimizing error, optimizing feature weights and evaluating the model against different metrics such as Accuracy, Precision, Recall, F1-score, Area Under the Curve (AUC) etc. Four supervised machine learning models such as Logistic Regression, Decision Tree, KNN and Random Forest are chosen as models to train and test with our dataset.

	* LOGISTIC REGRESSION:
		Logistic regression is a statistic that uses a logistic function to model a binary dependent variable. In regression analysis, logistic regression (or logit regression) is estimating the parameters of a form of binary regression. Mathematically, a binary logistic model has a dependent variable with two possible values which is represented by an indicator variable, where the two values are labeled either 0 or 1.
		
	* K-NEAREST NEIGHBOURS (kNN):
		The nearest neighbor (kNN) algorithm is a nonparametric classification method. Used for classification and regression. In either case, the input consists of the k closest training examples in the data set. Results depend on whether kNNs are used for classification or regression

	* DECISION TREE:
		A decision tree is a flowchart-like structure in which each inner node represents a "test" for an attribute (such as whether a coin toss is a heads or tails), each branch represents a test result, and each leaf node represents a class. brand. (Determined after calculating all properties). The path from root to leaf is a classification rule.

	* RANDOM FOREST:
		Random Forests or Random Decision Forests are ensemble training techniques for classification, regression, and other problems that work by constructing multiple decision trees during training. For classification problems, the output of a random forest is the class chosen from most trees. For regression problems, the mean or mean prediction of the individual trees is returned.
	
	
* Choosing Model Predictors:

From the Figure below, there is strong correlation between surprising factors like Drama which has negative correlation with our target variable.
Movies from Countries like Belgium, Luxembourg have positive correlation with our target variable.
Family centered genres like Animation, Comedy, Family have strong correlation with our target feature.
A heat map of correlation coefficients describes the measure of relationship between variables on one axis with the variables on the other axis. According to the palette used here, the lighter the color the greater the relationship. The correlation heat map shown in the figure 7 shows the top features, based on correlation with the Y-variable. These features were used as the predictor variable.

<p align="center"> 
	<img width="450" background= "red" alt="Picture1" src="https://user-images.githubusercontent.com/93501171/146659010-0b30a0e2-c02e-4b42-948b-60a108bfed97.png">
</p> 

<p align="center"> 
	<img width="839" alt="Screen Shot 2021-12-18 at 7 23 38 PM" src="https://user-images.githubusercontent.com/93501171/146659152-9719edb8-7992-432f-a338-3cfc1efe33d2.png">
</p> 

A basic model such as Logistic regression and kNN performed better with our dataset when compared to complex models like decision Tree.
The reason Decision Tree has the worst, among the four, evaluation metrics might be due to presence of outliers in our training set.


**To Conclude : **

* Initial Data Analysis gave some interesting and unexpected relationships. Like how United States movies have more ‘Non-Hit’ in comparison to other countries. This can be associated with the fact that the US has released a greater number of movies. Or how the genre “Drama” has negative correlation with whether a movie becomes a hit or not. It is also observed how Production Country has a strong correlation with our target variable. Features such as Production countries, specific genres, and the budget put into a movie also matters. Even though there are exceptions to each of the above-mentioned factors, in general, it is seen that a hit movie would have to be in one of the 8 genres.

* The metrics (mentioned in Table1) shows the Evaluation metrics that determine the fit of models to our dataset. The modelling showed that the simplest model, Logistic Regression, with the simplest of error calculation methods give the best model. It is expected that models such as Random Forest and Decision Tree would perform better, but it is seen that decision tree  has succumbed to outliers and exceptions and given the worst result out of the 4 models. Random Forest is not as sensitive to outliers but it still did not out-perform Logistic Regression, even if hyperparameters were tuned. 

* Hence, movie makers, producers, Film distributors can make use of these above-mentioned factors to decide if the movie will be a hit or not. However, there may be exceptions to each case mentioned. This may be attributed to other important factors that make a movie hit or not, such as Story, screenplay, actors etc. In future, the analysis could include text mining on the summary of a movie. This could make the model even more accurate.
