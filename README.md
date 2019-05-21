# Common Spanish Words
A learning tool to study the most frequently used Spanish words found in song lyrics as a way for non-Spanish speakers to learn the language in an efficient manner.

# Background
With thousands of words, the thought of learning another language can be daunting and overwhelming. Based on Tim Ferris' article, 12 Rules for Learning Foreign Languages in Record Time — The Only Post You’ll Ever Need (https://tim.blog/2014/03/21/how-to-learn-a-foreign-language-2/), the first rule is to focus one's time on learning the most common words in a new language. Ferris says, "20% of the effort you spend on acquiring new vocab could ultimately give you 80% comprehension in a language—for instance, in English just 300 words make up 65% of all written material. We use those words a lot, and that’s the case in every other language as well." This project will create a data-driven learning tool by identifying the most commonly used Spanish words found in Latin songs.

# Basis for Spanish Word Corpus 
As a point of comparison, the project compiled three datasets from open sources by scraping websites using read_html to download tables into Pandas. All code is written in Python in Jupyter Notebooks. 

The first dataset is a word corpus of 250 Spanish words from a Spanish learning dictionary taught in classrooms. The list seems to be arbitrarily compiled and contains no methodology for how the words were selected. The next two lists are 100-word corpora taken from Wikipedia.

The first 100-word corpus is an abbreviated list that was compiled by the Real Academia Española (RAE) to form a Reference Corpus of Current Spanish. The full list contains 160 million-word forms and was created from books, magazines, and newspapers with a wide variety of content, as well as transcripts of spoken language from radio and television broadcasts and other sources (published in June 2008).

The second 100-word corpus is an abbreviated list that was created by Mark Davies at Brigham Young University in 2006. It contains 20 million words compiled from 20th-century sources. About one-third (~6,750,000 words) come from transcripts of spoken Spanish: conversations, interviews, lectures, sermons, press conferences, sports broadcasts, and others. 
- https://github.com/yellow11marie/common-Spanish-words/blob/master/Spanish_Key_Updated.ipynb

# Collecting the Data 
Listening to music in a foreign language is an excellent way to deepen one’s listening comprehension as well as expand one's vocabulary. Lyrics from Latin songs are available online and relatively easy to download to form a Spanish word dataset. 

The data collection phase, first, consisted of downloading the names of Latin songs from Billboard.com. Each year, Billboard.com releases a list of the top 50 Latin songs, and from 2006 to 2018, the project collected 1,056 song names. Billboard.com did not have songs for years prior to 2006. To collect the song names, the project created a function that looped through all years and returned the artist name, rank, song title, and year into a data frame.  
- https://github.com/yellow11marie/common-Spanish-words/blob/master/Songs_List.ipynb

Tangentially, the project ran descriptive statistics on the most influential Latin artists. It returned value counts for the number of songs that each solo artist produced between 2006 and 2018 and plotted the artists in charts using Matplotlib and Seaborn. The top artist was La Arrolladora Banda el Limon de Rene Camacho with 22 songs appearing on the charts in the top 50 list by year, accounting for 2.08 percent of the share of total songs in 12 years. When the top 20 artists were segmented out, La Arrolladora Banda accounted for 7.91 percent of the total share of songs out of 20 artists. The project ran value counts for the number of times the top 20 artists appeared on the charts as a solo artist as well as a collaborator on other songs. Daddy Yankee was the top collaboration artist appearing in 43 songs, accounting for 10.51 percent of the share of the top 20 artists. 

The second phase of data collection consisted of downloading the lyrics for all 1,056 Latin songs from Genius.com. The project created a function that looped through all the years, song title, and artist and returned various data points, including lyrics, release year, artist, collaborator, etc., in a data frame. 
- https://github.com/yellow11marie/common-Spanish-words/blob/master/Lyrics_Genius_All.ipynb

# Text Cleaning 
From the dataset of song lyrics, the project cleaned and processed the lyrics text for analysis. It performed initial descriptive statistics on the lyrics and returned the number of capitalized words, numerals, word count, unique word count, and character count for each song. In a column for clean lyrics, the project removed punctuation and made the words lower case. This preprocessing makes working with text data easier and uniform.

From all 1,056 songs, the dataset returned a list of 26,977 Spanish words in total to form the basis of this project’s Spanish word corpus. 

Next, the project separated the lyrics into the different parts of speech using a national language processor, SpaCy, to identify nouns, verbs, pronouns, stop words, etc. SpaCy was also used to lemmatize the nouns and verbs. Lemmatization is the process of reducing nouns to their singular form, thus dropping the plural form as a duplicate, and retaining only the root infinitive verb by discarding various conjugations. The project ran value counts on each part of speech and rendered 6,729 lemmatized verbs (down from 10,264 verb forms), 9,960 lemmatized nouns (down from 11,231), 7,850 adverbs and adjectives, 424 pronouns, 741 stop words, and 248 conjunctives. Separate word clouds display the word list for each part of speech. 
- https://github.com/yellow11marie/common-Spanish-words/blob/master/Spanish_Words_Dataset.ipynb 

# Analysis of Findings
The project compares an abbreviated list of 250 Spanish words created from lyrics to the 250-word Spanish key and both 100-word Spanish corpora from Wikipedia. The project returned each dataset into a bog of words for side by side comparison and returned similarities and differences. 

The findings from the comparison are as follows:

- There were only 105 word similarities between the 250 Lyrics corpus and the original 250 Spanish key. Stop words were not removed. Based on word frequency, the lists were not very similar.
- The Lyrics corpus had to be cleaned to exclude English words, numbers, and artist names. This corpus did not include lemmatized nouns and verbs, thus containing similar and/or repetitive word forms. The Lyrics corpus also contained a handful of nouns that refer to sex, love, and relationships. For example, heart, love, lips, body, kiss, mouth, bed, etc. These words accounted for 25 of the 149 word differences between the Lyrics corpus and Spanish key (16.7%).
- The Spanish key included 56 verbs out of the 147 word difference (38%) that were not present in the 250 word Lyrics corpus. This supports the hypothesis that the Spanish key was compiled from/for a classroom-style learning format.
- When the two Spanish word corpora from Wikipedia were compared, out of 100 words, the two lists contained 34 different words (34%). Comparing the differences was more revealing than the similarities. The first Spanish word corpus did not have its verbs lemmatized into the infinitive form, thus containing multiple tenses and conjugations. The second Spanish word corpus contained only verb infinitives, and 22 of the 36 differences were verb infinitives (61%).
- Comparing a second abbreviated 100-word Lyrics corpus to the first Spanish word corpus from Wikipedia, the two lists had 59 similarities. The main differences were nouns, same as mentioned above. Interestingly, the first Spanish word corpus had nouns such as government and country, words found in the news or formal writing.
- The 100-word Lyrics corpus was less similar to the second Spanish word corpus, containing only 49 similarities.

Next, the project compared the value counts of the separate parts of speech to the total Lyrics word corpus. 

- 26,977 total words in the lyrics corpus. When divided into the parts of speech, SpaCy returns 25,211 words.
- 9,960 lemmatized nouns, 6,729 lemmatized verbs, 7,850 adverbs and adjectives, 424 pronouns, and 248 conjunctives.
- Nouns represent 39.5% of the total words, 24.9% are verbs, 29.1% adverbs and adjectives, 1.6% are pronouns, 0.9% are conjunctives.
- Of a list continuing 250 words, the share of nouns would be 99, 63 verbs, 73 adverbs and adjectives, 4 pronouns, and 2 conjunctives. 
- The share of the total are displayed in a Seaborn chart.

- https://github.com/yellow11marie/common-Spanish-words/blob/master/Spanish_Analysis.ipynb

# Data Visualization
The project uses data visualizations at various stages and can be found in the follow:
- Under the songs list, the most influential artists are displayed and compared by number of top songs in matplotlib and seaborn.
- Under text analysis, the SpaCy parts of speech tagger has a built-in display for the types of words (nouns, verbs, stop words, etc.) within the lyrics.
- Under text cleaning, each part of speech is displayed in a separate Word Cloud.
- Under analysis, the common Spanish words are displayed in bar charts.

# Conclusion and Applications for Spanish Learners
Updated Hypothesis:
- Compiling lyrics will render a useful set of 250-300 most commonly used Spanish words 
    - >UPDATED: The Lyrics corpus is useful but should be combined with the other corpora to form a comprehensive list of 500 common Spanish words. 
- The assumption is that the lyrics corpus will have limitations, namely that it does not include nouns that are esential for traveling - ordering food, transportation, greetings, etc. These topics will need to be learned in addition to the list if traveling to a Spanish speaking country, but not necessarily relevant to having a conversation with a Spanish speaker. 
    - >UPDATED: True, but when combined with the classroom corpus more topics are covered. Additional nouns would be beneficial for travel, but not necessarily in conversations with Spanish speakers.
- The lyrics corpus will have a greater percent of words related to love, sex, and relationships, as that its often the topic of songs. 
    - >UPDATED: True. This remains important as conversational topic. 
    
RESULT:
- Start studying the 500 Spanish word list today to become conversationally fluent in no time.

# Further Analysis
1. The SpaCy parts of speech tagger had errors, particularly with compound words that are more frequently found in Spanish than English. For example, the word ‘dimelo’—translation: give it to me—was tagged as a noun. It also did not exclude English or Portuguese words or numbers. The lyrics dataset required additional cleaning, which could be achieved by creating a machine learning algorithm to detect the current errors and train a new model to be deployed on the lyrics dataset. This was not essential to complete the project, as the 500 word list could be cleaned by hand in a more expedient manner than creating a learning model. However, for future projects a new model for SpaCy Spanish would be useful.

2. While the initial project was to analyze word frequencies, parts of speech, and come up with a list of common words, a spin-off project could be undertaken on the meaning of the lyrics. Creating a sentiment analysis classifier for the song lyrics would be interesting. It would require building a sentiment classifier, polarity or subjectivity, for Spanish. One could also build a classifier for emotion detection using Scikit-learn. This spin-off project will be added as it develops. 
