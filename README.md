# Feature-Analysis
Analyzing variables modeling clean data to determine factors that contribute to the success rate of a movie.


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








