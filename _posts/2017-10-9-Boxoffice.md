---
layout: post
title: Let's go see a movie!
---

For my next project, I wanted to see if I could predict the opening weekend
box office results of a movie based on some characteristics about the movie.
The project began by collecting some movie box office data via web scraping. I
used Beautiful Soup as my web-scraping tool. The bulk of my data was scraped
from the website boxofficemojo.com. In order to fill in some data gaps, I also
scraped movie budget data from the-numbers.com.  

After gathering the various bits of data. I spent some time using python,
specifically pandas, to clean the scraped data into a single data frame. One of
my biggest challenges was joining the data scraped from the two websites. While
the title fields were very similar, small discrepancies in formatting or
punctuation prevented an exact match on all titles. Additionally, since multiple
movies could have the same title, I needed to consider the release data of the
film in my data joins.  

In order to increase the resulting matches across the two sets and to keep from
losing unnecessary data rows in the merge, I installed and used fuzzywuzzy to
get the best scored match for each record in the the-numbers.com dataset. Once
all the data was linked into a single data frame, I created some dummy indicator
variables for a few of the categorical features in my movie characteristics
dataset. For example, rather than using all franchise/series names, I made a
single 1/0 column to indicate whether or not the movie was part of a franchise.  

Once all my categorical features had been transformed into dummy variables, I
used statsmodels to run a linear regression on some of the remaining features.
After some feature selection, I was able to create a model with around a .65
r-squared value. I performed cross-validation using a 70/30 train-test split and
achieved similar results. My final model take the following features: budget,
number of opening theaters, movie runtime, franchise indicator, Summer/Winter
release indicator.  

Full details on the project can be found at my github repo: kandice4/boxoffice.
