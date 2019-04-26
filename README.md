# Common Spanish Words
A learning tool to study the most frequently used Spanish words found in song lyrics as a way for non-Spanish speakers to learn the language in an efficient manner.

# Background
With thousands of words, the thought of learning another language can be daunting and overwhelming. Based on Tim Ferris' article, 12 Rules for Learning Foreign Languages in Record Time — The Only Post You’ll Ever Need (https://tim.blog/2014/03/21/how-to-learn-a-foreign-language-2/), the first rule is to focus one's time on learning the most common words in a new language. Ferris says, "20% of the effort you spend on acquiring new vocab could ultimately give you 80% comprehension in a language—for instance, in English just 300 words make up 65% of all written material. We use those words a lot, and that’s the case in every other language as well." This data-driven learning tool will identify the most commonly used Spanish words in Latin songs.

# Hypothesis 
Identify a list of Spanish words to form the basis of comparison. The initial 250 Spanish words list was taken from an online Spanish learning dictionary that reflects a classroom taught vocaulary list. As a secondary test, two more word corpora were taken from Wikipidia. 

The first is an abbreviated list of top 100 words that was compiled by the Real Academia Española (RAE) to form a  Reference Corpus of Current Spanish. It contains 160 million word forms and was taken from books, magazines, and newspapers with a wide variety of content, as well as transcripts of spoken language from radio and television broadcasts and other sources (published in June 2008). 

The second was created by Mark Davies at Brigham Young University in 2006. This corpus contains 20 million words compiled from 20th-century sources. About one-third (~6,750,000 words) come from transcripts of spoken Spanish: conversations, interviews, lectures, sermons, press conferences, sports broadcasts, and so on. Notebook listed below.
- https://github.com/yellow11marie/common-Spanish-words/blob/master/Spanish_Key_Updated.ipynb

# Collecting the Data 
Pop culture found in music and film are an excellent way to learn listening comprehension as well as expand one's vocabulary when learning a language. Examining Latin music lyrics will test the hypothesis. Latin song lyrics are more readily available (as opposed to film scripts). The data collection phase, first, consisted of downloading a list of top Latin songs from Billboard.com. 
- https://github.com/yellow11marie/common-Spanish-words/blob/master/Songs_List.ipynb

The second pahses consisted of downloading the lyrics for all Latin songs from Genius.com. The lyrics word corpus was exported into a dataframe for analysis. 
- https://github.com/yellow11marie/common-Spanish-words/blob/master/Lyrics_Genius_All.ipynb

# Text Cleaning 
From the dataset of songs, the text was cleaned and processed. Initial descriptive statistics were run, rendering a list of 26,977 Spanish words found in 1,054 songs from 2006 to 2018. Next, the lyrics were separated into the different parts of speech using a national language processor, SpaCy, to identify nouns, verbs, pronouns, stopwords, etc. SpaCy was also used to lemmatize the nouns and verbs. Lemmatization is the process of reducing nouns to their singular form, thus dropping the plural form as a duplicate, and retaining only the root infinitive verb by discarding various conjugations.

- https://github.com/yellow11marie/common-Spanish-words/blob/master/Spanish_Words_Dataset.ipynb 

# Analysis of Findings
Qualitative Review of List Comparison:
   - There are only 105 word similarities between the 250 Lyrics corpus and the original 250 Spanish key and 149 word differences. Based on word frequency, the lists are not very similar. 
   - The Lyrics corpus had to be cleaned to exclude English words, numbers, proper names, and some slang. This corpus did not include lemmatized nouns and verbs, thus containing similar and/or repatiitve words and meanings. The Lyrics corpus also contains a handful of nouns that refer to sex, love, and relationships (as was expected and supports the hypothesis). For exmaple, heart, love, lips, body, kiss, mouth, bed, etc. This accounted for roughly 25 of the 149 difference in the Lyrics corpus (16.7%).
   - What was excluded from the Spanish key were primarily verbs. The Spanish key included 56 verbs out of the 147 word difference (38%) that were not present in the 250 word Lyrics corpus. This supports the hypothesis that the Spanish key was compiled from/for a classroom-style learning format. 
   - When the two Spanish word corpora were compared, out of 100 words, the two lists contianed 34 different words (34% or 1/3 of the lists). Comparing the differences was more revealing than the similarities. The Spanish word corpus 1 did not have its verbs lemmatized into the infinitive form, thus containing multiple tenses and conjugations. The Spanish word corpus 2 contained only verb infinitives, and 22 of the 36 differences were verb infinitives (61% or two thirds). 
   - Comparing the 100 word Lyrics corpus to the Spanish word corpus 1, thw two lists had 59 similarities. The main differences were nouns, same as mentioned above. Interestingly, the Spanish word corpus 1 had nouns such as government and country, words found in the news or formal writing. 
   - The 100 word Lyrics corpus was less similar to the Spanish word corpus 2, containing 49 similarities. 
- https://github.com/yellow11marie/common-Spanish-words/blob/master/Spanish_Analysis.ipynb

# Data Visualization
Data visualizations are displayed at various stages. 
- Under the songs list, the most influencial artists are displayed and compared by number of top songs in matplotlib and seaborn.
- Under text analysis, the SpaCy parts of speech tagger has a biult-in display for the types of words (nouns, verbs, stopwords, etc) within the lyrics. 
- Under text cleaning, each part of speech are displayed in a separate Word Cloud.
- Under analysis, the common Spanish words are disaplyed in bar charts. 

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

# Further Analysis (Forthcoming)
1. The SpaCy parts of speech tagger had errors, particularly with compound words that are more frequent in Spanish. It also did not exclude English words or numbers. Overall, the lyrics dataset needs further cleaning by creating a machine learning algorithm to detect the current errors and train a new model to be deployed on the lyrics dataset. 

2. While the initial project was to analyze word frequencies, parts of speech, and come up with a list of commmon words, this project could be taken a step further. A second machine learning model could be created for Spanish to test and validate the sentiment in the lyrics, and compare the sentiment to the other Spanish word corpora. 
