# Common Spanish Words
A learning tool to study the most frequently used Spanish words found in song lyrics as a way for non-Spanish speakers to learn the language in an efficient manner.

# Background
With thousands of words, the thought of learning another language can be daunting and overwhelming. Based on Tim Ferris' article, 12 Rules for Learning Foreign Languages in Record Time — The Only Post You’ll Ever Need (https://tim.blog/2014/03/21/how-to-learn-a-foreign-language-2/), the first rule is to focus one's time on learning the most common words in a new language. Ferris says, "20% of the effort you spend on acquiring new vocab could ultimately give you 80% comprehension in a language—for instance, in English just 300 words make up 65% of all written material. We use those words a lot, and that’s the case in every other language as well." This project will create a data-driven learning tool by identifying the most commonly used Spanish words found in Latin songs.

# Basis for Spanish Word Corpus 
As a point of comparison, the project compiled three datasets from open sources by scraping websites using read_html to download tables into Pandas. All code is written in Python in Jupyter Notebooks. 

The first dataset was a word corpus of 250 Spanish words from a Spanish learning dictionary taught in classrooms. The list seemed to be arbitrarily compiled and contained no methodology for how the words were selected. The next two lists were 100-word corpora taken from Wikipedia.

The first 100-word corpus was an abbreviated list that was compiled by the Real Academia Española (RAE) to form a Reference Corpus of Current Spanish. The full list contains 160 million-word forms and was created from books, magazines, and newspapers with a wide variety of content, as well as transcripts of spoken language from radio and television broadcasts and other sources (published in June 2008).

The second 100-word corpus was an abbreviated list that was created by Mark Davies at Brigham Young University in 2006. It contains 20 million words compiled from 20th-century sources. About one-third (~6,750,000 words) come from transcripts of spoken Spanish: conversations, interviews, lectures, sermons, press conferences, sports broadcasts, and others.
- Spanish_Key_Updated.ipynb

# Collecting the Data 
Listening to music in a foreign language is an excellent way to deepen one’s listening comprehension as well as expand one's vocabulary. Lyrics from Latin songs are available online and relatively easy to download to form a Spanish word dataset. 

The data collection phase, first, consisted of downloading the names of Latin songs from Billboard.com. Each year, Billboard.com releases a list of the top 50 Latin songs, and from 2006 to 2018, the project collected 1,056 song names (there were no songs listed prior to 2006). To collect the song names, the project created a function that looped through all years and returned the artist name, rank, song title, and year into a data frame.   
- Songs_List.ipynb

Tangentially, the project ran descriptive statistics on the most influential Latin artists. It returned value counts for the number of songs that each solo artist produced between 2006 and 2018 and plotted the artists in charts using Matplotlib and Seaborn. The top artist was La Arrolladora Banda el Limon de Rene Camacho with 22 songs appearing on the charts in the top 50 list by year, accounting for 2.08 percent of the share of total songs in 12 years. When the top 20 artists were segmented out, La Arrolladora Banda accounted for 7.91 percent of the total share of songs out of 20 artists. The project ran value counts for the number of times the top 20 artists appeared on the charts as a solo artist as well as a collaborator on other songs. Daddy Yankee was the top collaboration artist appearing in 43 songs, accounting for 10.51 percent of the share of the top 20 artists. 

The second phase of data collection consisted of downloading the lyrics for all 1,056 Latin songs from Genius.com. The project created a function that looped through all the years, song title, and artist and returned various data points, including lyrics, release year, artist, collaborator, etc., in a data frame.  
- Lyrics_Genius_All.ipynb

# Text Cleaning 
From the dataset of song lyrics, the project cleaned and processed the lyrics text for analysis. It performed initial descriptive statistics on the lyrics and returned the number of capitalized words, numerals, word count, unique word count, and character count for each song. In a column for clean lyrics, the project removed punctuation, numbers, consecutive duplicate words, the artists' names, and made the words lower case. English songs and words also had to be removed. 

From all 1,056 songs, the dataset returned a list of 26,977 Spanish words in total to form the basis of this project’s Spanish word corpus. 

Next, the project separated the lyrics into the different parts of speech using the national language processor, SpaCy, to identify nouns, verbs, pronouns, stop words, etc. SpaCy was also used to lemmatize the nouns and verbs. Lemmatization is the process of reducing nouns to their singular form, thus dropping the plural form as a duplicate, and retaining only the root infinitive verb by discarding various conjugations. The project ran value counts on each part of speech and rendered 6,705 lemmatized verbs (down from 10,264 verb forms), 9,843 lemmatized nouns (down from 11,110), 8,022 adverbs and adjectives, 733 stop words, 445 pronouns, and 252 conjunctives. Separate word clouds display the prominence of each part of speech. 
- Spanish_Words_Dataset.ipynb 

# Analysis of Findings
The project compared an abbreviated list of 100, 250, and 500 Spanish words created from lyrics to the 250-word Spanish key and both 100-word Spanish corpora from Wikipedia. The project converted each dataset into a bag of words for side by side comparison and returned their similarities and differences. 

Detailed findings from the comparison are as follows:

- There were only 105 word similarities between the 250 Lyrics corpus and the original 250 Spanish key. Stop words were not removed. Based on word frequency, the lists were not very similar.
- The Lyrics corpus had to be cleaned to exclude English words, numbers, and artist names. This corpus did not include lemmatized nouns and verbs, thus containing similar and/or repetitive word forms. The Lyrics corpus also contained a handful of nouns that refer to sex, love, and relationships. For example, heart, love, lips, body, kiss, mouth, bed, etc. These words accounted for 25 of the 149 word differences between the Lyrics corpus and Spanish key (16.7%).
- The Spanish key included 56 verbs out of the 147 word difference (38%) that were not present in the 250 word Lyrics corpus. This supports the hypothesis that the Spanish key was compiled from/for a classroom-style learning format.
- When the two Spanish word corpora from Wikipedia were compared, out of 100 words, the two lists contained 34 different words (34%). Comparing the differences was more revealing than the similarities. The first Spanish word corpus did not have its verbs lemmatized into the infinitive form, thus containing multiple tenses and conjugations. The second Spanish word corpus contained only verb infinitives, and 22 of the 36 differences were verb infinitives (61%).
- Comparing a second abbreviated 100-word Lyrics corpus to the first Spanish word corpus from Wikipedia, the two lists had 59 similarities. The main differences were nouns, same as mentioned above. Interestingly, the first Spanish word corpus had nouns such as government and country, words found in the news or formal writing.
- The 100-word Lyrics corpus was less similar to the second Spanish word corpus, containing only 49 similarities.

Next, the project compared the value counts of the separate parts of speech to the total Lyrics word corpus. 

- 26,977 total words in the lyrics corpus, 26,106 without English stop words. When segmented into the parts of speech, SpaCy returned 26,000 words.
- 9,843 lemmatized nouns, 6,705 lemmatized verbs, 8,022 adverbs and adjectives, 733 stop words, 445 pronouns, and 252 conjunctives.
- Nouns were 37.85%, 25.78% verbs, 30.85% adverbs and adjectives, 2.8% stop words, 1.7% pronouns, and 0.9% conjunctives.
- Of a list continuing 500 words, the share of nouns would be 189.25, 128.9 verbs, 154.25 adverbs and adjectives, 14 stop words, 8.5 pronouns, and 4.5 conjunctives.
- The share of the totals were displayed in a Seaborn chart.

- Spanish_Analysis.ipynb

# Data Visualization
The project used data visualizations at various stages and can be found in the following:
- Under the songs list, the most influential artists were displayed and compared by number of top songs in matplotlib and seaborn.
- Under text analysis, SpaCy has a built-in display. This was customized for the different parts of speech (nouns, verbs, stop words, etc.) within the lyrics.
- Under text cleaning, each part of speech was displayed in a separate Word Cloud.
- Under analysis, the common Spanish words were displayed in bar charts.


# Conclusion and Applications for Spanish Learners
Hypothesis vs Findings:
- Compiling lyrics will render a useful set of 250-300 most commonly used Spanish words 
    - UPDATED: The Lyrics corpus was expanded to a comprehensive list of 500 common Spanish words broken down into lemmatized nouns, lemmatized verbs, stop words, pronouns, adjectives and adverbs, and conjunctions by their share of words found in the total lyrics word corpus.
- The assumption is that the lyrics corpus will have limitations, namely that it does not include nouns that are essential for traveling - ordering food, transportation, greetings, etc. These topics will need to be learned in addition to the list if traveling to a Spanish speaking country, but not necessarily relevant to having a conversation with a Spanish speaker. 
    - UPDATED: True. Additional nouns would be beneficial for travel.
- The lyrics corpus will have a greater percent of words related to love, sex, and relationships, as these are often the topic of songs. 
    - UPDATED: True. These words remain important to learn as they are frequently used in conversations. 

RESULT:
- Start studying the 500 Spanish word list today. Supplement your learning with travel vocabulary and learn the conjugations of common verbs. More importantly, listen to Latin music while you’re learning. 

Supporting Data
- To supplement the 500 Spanish word list (or unigram), additional ngrams were run on the lyrics word corpus, including bigrams, trigram, and quadrigrams all the way up to decagram. Ngram lists ere compared with stop words and without. Additional text cleaning was required. The songs needed to be divided into up by the chorus and verses, and duplicate sections needed to be removed for a more accurate understanding of common ngrams. The supplemental data analysis rendered additional lists of word patterns consisting of two, three, four, and more words. This is a potential basis for a language teaching model.

- N-grams.ipynb

# Further Analysis
1.	The SpaCy parts of speech tagger had errors, particularly with compound words that are more frequently found in Spanish than English. For example, the word ‘dimelo’—translation: give it to me—was tagged as a noun. 
    - UPDATED: At the time of this writing, SpaCy does not have a function to update only a set of words and add to the existing language model. To update the errors in compound words with a verb stem, an entire new Spanish model would need to be added. 

2.	While the initial project was to analyze word frequencies and parts of speech, a spin-off project could be undertaken on the meaning of the lyrics. Creating a sentiment analysis classifier for the song lyrics would be fascinating. It would require building a sentiment classifier, polarity or subjectivity, for Spanish. One could also build a topic modeler for emotion detection using Scikit-learn. 
    - UPDATED: While NLTK/TexBlob has a built-in sentiment analyzer for the English language, there is not one for Spanish at the time of this writing. A custom Spanish sentiment analyzer would need to be built and individually tagged 10,000-20,000 sentences with sentiment. This could be achieved by compiling a new dataset from social media, Twitter or Facebook. Potential issues could be the presence of slang, differing sentiment or meaning between dialects, and the level of specificity required for a sentiment analyzer or topic modeler. 

