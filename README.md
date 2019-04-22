# Common Spanish Words
A learning tool to study the most frequently used Spanish words found in song lyrics as a way for non-Spanish speakers to learn the language in an efficient manner.

# Background
With thousands of words, the thought of learning another language can be daunting and overwhelming. Based on Tim Ferris' article, 12 Rules for Learning Foreign Languages in Record Time — The Only Post You’ll Ever Need (https://tim.blog/2014/03/21/how-to-learn-a-foreign-language-2/), the first rule is to focus one's time on learning the most common words in a new language. Ferris says, "20% of the effort you spend on acquiring new vocab could ultimately give you 80% comprehension in a language—for instance, in English just 300 words make up 65% of all written material. We use those words a lot, and that’s the case in every other language as well." This data-driven learning tool will identify the most commonly used Spanish words in Latin songs.

# Hypothesis 
Download a list of 250 common Spanish words to form a hypothesis. The initial Spanish words list was taken from an online Spanish learning dictionary that reflects a classroom taught vocaulary list. As a secondary test, two more word corpora were taken from Wikipidia. Notebooks listed below.
- https://github.com/yellow11marie/common-Spanish-words/blob/master/Spanish_Key_Updated.ipynb

# Collecting the Data 
Pop culture found in music and film are an excellent way to learn listening comprehension as well as expand one's vocabulary when learning a language. Examining Latin music lyrics will test the hypothesis. Latin song lyrics are more readily available (as opposed to film scripts). The data collection phase, first, consisted of downloading a list of top Latin songs from Billboard.com. 
- https://github.com/yellow11marie/common-Spanish-words/blob/master/Songs_List.ipynb

The second pahses consisted of downloading the lyrics for all Latin songs from Genius.com. The lyrics word corpus was exported into a dataframe for analysis. 
- https://github.com/yellow11marie/common-Spanish-words/blob/master/Lyrics_Genius_All.ipynb

# Text Cleaning 
-describe what i did here ...
Initial text analysis has been performed on a sample of four Latin song lyrics. 

Text analysis includes two phases: the first runs descriptive statistics on the lyrics and identifies the the word count, unique word count, and their frequencies. The second phase uses SpaCy Spanish to divide the lyrics into various parts of speech, including nouns, verbs, pronouns, stopwords, etc. It also lemmatizes the verbs down to their root form and drop duplicates.
- https://github.com/yellow11marie/common-Spanish-words/blob/master/Spanish_Words_Dataset.ipynb 

# Analysis of Findings

# Data Visualization
Data visualizations are displayed at various stages. 
- Under the songs list, the most influencial artists are displayed and compared by number of top songs in matplotlib and seaborn.
- Under text analysis, the SpaCy parts of speech tagger has a biult-in display for the types of words (nouns, verbs, stopwords, etc) within the lyrics. 
- Under text analysis, each part of speech have been displayed in a separate Word Cloud.

# Conclusion and Applications for Spanish Learners
- This section will be concluded after all the lyrics have been compiled from Genius.com.

# Further Analysis (Forthcoming)
1. The SpaCy parts of speech tagger had errors, particularly with compound words that are more frequent in Spanish. It also did not exclude English words or numbers. Overall, the lyrics dataset needs further cleaning by creating a machine learning algorithm to detect the current errors and train a new model to be deployed on the lyrics dataset. 

2. While the initial project was to analyze word frequencies, parts of speech, and come up with a list of commmon words, this project could be taken a step further. A second machine learning model could be created for Spanish to test and validate the sentiment in the lyrics, and compare the sentiment to the other Spanish word corpora. 
