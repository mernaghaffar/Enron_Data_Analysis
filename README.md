# Enron_Data_Analysis Using Natural Language Processing (NLP)
Author2Topic Analysis of Enron Dataset

NLP Analysis


Person-Topic Feature
_______________________

Here to goal is to be able to extract and generalize the topic of conversation within a communication platform (email , chat, etc.)
This feature is derived from the use of The author-topic model, which is typically used to get insights about authors of papers. 
The theoretical explanation behind this model can be found here <https://mimno.infosci.cornell.edu/info6150/readings/398.pdf> . The author-topic model is an extension of Latent Dirichlet Allocation (LDA), which allows us to learn topic representations of authors in a corpus. The model can be applied to any kinds of labels on documents, such as tags on posts on the web. The model can be used as a novel way of data exploration, as features in machine learning pipelines, for author (or tag) prediction, or to simply leverage your topic model with existing metadata.

Tool written in Python.

The jupyter notebook starts off with the loading, parsing and cleaning of eml files (from _sent_mail folder to start as working example).Then proceeds to construct a mapping from author names (which actually in our case is the send "To") to email_ids. Before feeding the content to the model, the texts needed pre-processing.

The following steps were taken for pre-processing (most of the work done by Spacy (a super great python package):
1. Tokenizing text.
2. Replacing all whitespace by single spaces.
3. Remove all punctuation 
4. Remove stopword
5. Lemmatize words
6. Add multi-word named entities
7. Add frequent bigrams (via Genism)
8. Remove frequent and rare words

The text is vectorized by computing bag-of-words.
I load the AuthorTopicModel, but before working with it I train several models with different random initializations, by giving different seeds for the random number generator (random_state). Then evaluate the topic coherence of the model (Topic Coherence measures score a single topic by measuring the degree of semantic similarity between high scoring words in the topic) and pick the model with the highest topic coherence to work with.
Then finally we get to explore the author-topic representation! I sorted the people (by count) that were mentioned in the emails and selected the top 10. This tool allows to explore the topics that mostly resonates with the person (based on history of emails (in this case only the _sent_mail folder).

A second .ipynb files looks at parsing the html files from chat communication. While the current notebook sucessfully parses conversation between 2 people, more work is needed to work with 3 or more people. However once implemented, it should follow the same sequence as the original .ipynb file.


Future Work:

There is more work I would've implemented but wasn't able to due to lack of time.
1. Further cleaning of parsed dataframe; separating the first name, last name from emails
2. merge all files from all directories and train the model in that based
3. Use the information from data exploration and from the author2doc model to create a Social Network Analysis to better visualized the relationships (and common words/topics) between P Allen and others.
4. Compare the nature of relationships P Allen with people he communicated with frequently vs non-frequently (by comparing topic dominance in both).

