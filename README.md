# lyric-analysis
This notebook explores different Topic Modelling techniques to create a song recommender based solely on lyrical analysis.

The recommender app can be seen [here](https://song-recommendation-by-lyrics.herokuapp.com/). The final model used an LDA topic modelling system.

## Data
I grabbed the artists from scraping pages at [ranker.com](https://www.ranker.com/), a crowd-sourced rankings site.

I used selenium and beutiful soup to scrape the web pages.

I then used [this python library](https://github.com/johnwmillr/LyricsGenius), to help grab the songs and lyrics from [Genius.com](https://genius.com/), a website with lyrics for practically every song. 

I stored all of my data in a postgres database. I hooked that database up to my heroku app to use for the recommender.

## Project Goal
The ultimate goal is to create a recommendation system based purely on song lyrics. For this project I only used classic rock songs because of time and storage restraints, but ultimately the goal would be to create a tool that helped people explore new genres.


## Important Files

- [Artist_Scraper.ipynb](workbooks/Artist_Scraper.ipynb)\
  notebook containing the process of scraping ranker.com to grab the artist information. 
  
- [Pull_Songs.ipynb](workbooks/Pull_Songs.ipynb)\
  notebook containing the process of pulling each song and its lyrics for every artist. 
  
- [EDA_1_LSA_NMF.ipynb](workbooks/EDA_1_LSA_NMF.ipynb) and [EDA_2_LDA.ipynb](workbooks/EDA_2_LDA.ipynb)\
  notebooks containing the topic modelling processes for LSA, NMF, and LDA  
  
- [Full_workflow.ipynb](workbooks/Full_workflow.ipynb)\
  This final notebook contains the full workflow from vectorizing to topic modelling, to creating a recommender
  
  
  
## Vectorizers and Topic Modelling methods Explored
- Count Vectorizers
- TFIDF Vectorizers 

- LSA topic modelling
- NMF topic modelling
- LDA topic modelling
  

## Biggest Challenge

The first challenge was deciding how many topics to model for. With too many topics the words associated with each topic felt less and less "conected" and it was harder to "explain" each topic. With too little topics, each topic because too borad and exncompaased too many ideas. It became a balancing act with number of topics.

In addition to picking the number of topics, I also had to decide which stop words to remove. Words like "to", "the", and "it" are obvious words to remove as they don't really add any meaning to the song. However, words like "come", "tell", and "try" were all less obvious stop words that I eneded up removiong when i was analysing the topics. 

Lastly I removed words that appeared in too many or too few of the songs from my modelling. The cutoff percentage of what "appearing in too many or too few songs" meant was another variable that I had to tune. I ended up deciding that words appearing in over half the songs would be removed and words appearing in less than 3 percent of the songs woud be removed. 

Adjusting any of the above could have big impacts on the topics produced. It took a lot of trial and error to get everything right where I felt like I was getting the ideal topic breakdown for my recommender. 
  

  
## Final Model In Action
[Here](https://song-recommendation-by-lyrics.herokuapp.com/) you can play with the final model in action.


## Technologies/Programs used
- Python
- Pandas/NumPy
- SQL/Postgres/psycopg2
- Flask
- Javascript
- Heroku

