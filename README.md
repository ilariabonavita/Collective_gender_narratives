# Collective gender narratives, a text mining analysis

This project presents an NLP analysis of a dataset of texts collected by the Eurepean Institute for Gender Equality (EIGE) in a "A study of collected narratives on gender perceptions in the 27 EU Member States". The approach adopted in the original study is mostly qualitative therefore I propose here some experiments for a quantitative approach to the analysis. It is a preliminary analysis and several improvements can be envisaged in all the parts of the pipeline. The dataset is publicly available on the institute database repository https://eige.europa.eu/gender-statistics/dgs. The database is a mx4, containing the raw text data, metadata and other variables and it can be read through MAXQDA software, which allows storage, retrieval and analysis of texts, based on code words. 

## Database preprocessing
To allow an easier data manipulation in Python and R, I merged the text and the other variables in a csv file, available in the ./data/df_all.tsv. In this file, each row is uniquely identified by the code present in "Document_name" column. The format of the code is as following "AT_Q_F_21_CFR" where the first chuck is the code of the State member, the second refers to whether the document contains quotes (Q) from the interview or the all narrative/interview (N), the third is the sex of the interviewed participant, the forth is the age of the participant and the fifth is a code indicating the topic of the narrative. For the dictionary of the codes-topics and the meaning of the other columns, please refer to the study documentation (find the report in ./data). The column "text" contains the text object of the analysis. The database provides the complete narratives/interviews in the native language of the participants and an extract, in English, of some relevant parts of the interview (Quotes). For the analysis I only considered text in English, therefore only the quotes have been used. Moreover, I removed the part of text referring to the interviewers speech. In this way, the column "text" marges the parts of speech of the participants in the study, extracted from the quotes documents. Additionally, for less intense computations, I provide a smaller dataset  (./data/df2.tsv) where in the 'text' column, only the longer part of speech present in the quote document is collected.

## Analysis
To make sure to have all the needed packages, you can recreate the environment provided in gender.yml.
The main packages needed for the analysis are NLTK, spacy and gensim.

The following techniques have been tried:
- Topic modelling with LDA
![alt text](http://img/topic_modeling_lda.png)

- Sentiment analysis
- Word clouds generation
- Entity analysis to extract noun-adjectives pairs of interest (e.g. adjectives related to the word "woman").
