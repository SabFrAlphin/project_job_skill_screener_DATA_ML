# Linkedin job ad analysis

## Objective:
1) Analyse word clusters in job title and job text based on distinct job_class
- Data Scientist
- Data Analyst
- Data Engineer

2) Train a SVM machine learning model to recognize distinct job titles

3) Analyse and 3D visualisation on how distinct the job titles are used in the Berlin tech job market using PCA and t-SNE

## Structure:
'job_data_preprocessing.ipynb'
- collecting data from the postgres data base (see Part I)
- Manually classifying the job ads based on their title into the three distinct categories
- job_text and job_title language to be translated into english
- text pre-processing
    - lowercasing text
    - removing special text (\n, \r, \t)
    - removing punctuation
    - removing stopwords
    - tokenizing
    - generating n-grams
    - stem words
    - lemmatize words
