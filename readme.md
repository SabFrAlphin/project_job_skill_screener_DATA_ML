# Linkedin job ad analysis

## Objective:
Analyse the Berlin tech job market and evaluate how distinct job profiles for the following roles:
- Data Scientist
- Data Analyst
- Data Engineer

1) Analyse word clusters in job title and job text based on distinct job_class

2) Train a SVM machine learning model to recognize distinct job titles

3) Analyse and 3D visualisation on how distinct the job titles are used in the Berlin tech job market using PCA and t-SNE

## Data:
- dataset has 969 job entries
- doublicates have been removed based on linked_in job id
- caution: If job is re-posted or posted in several languages, might still be included

## Structure:
'job_data_preprocessing.ipynb'
- collecting data from the postgres data base [see Part I](https://github.com/SabFrAlphin/project_job_skill_screener_SCRAPING)
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
## Analysis:

- most Berlin jobs are in Data Engineering --> this is also due to a large overlap with software engineer roles in the dataset
![count plot](/99_data/count_plot.png)

- Zalando, delivery hero, amazon and charitee have most job openings in the last 3-4 weeks
- this is not a total number of openings, but an indicator of job marketing spend of the company
![company plot](/99_data/company_plot.png)

- Around 67% of advertised jobs are open for entry level positions and some experience
![seniority plot](/99_data/seniority_plot.png)

1) __Analyse word clusters__
- Analysis of the top 20 tfidf words, shows differences between the 3 distinct roles
- Example: infrastructure is most important for Data Engineers, least for Data Scientists
![tfidf plot](/99_data/tfidf_plot.png)

- Visualisation of top 20 common/ unique words as a heatmap
![tfidf heatmap](/99_data/tfidf_heatmap.png)

- topic cluster distinction using a LDA model, shows topics can be seperated
![lda model](/99_data/LDA_model.jpeg)

2) __Train a SVM machine learning model - supervised learning__
- Training a supervised SVM model shows a training accuracy of 98.7%
- Since the y-labels (job_class) have been manually imputed, the model only learns somewhat incorrect information and replicates it on new data
![svm test](/99_data/svm_test.jpeg)
![confusion](/99_data/confusion_test.png)


3) __2D/3D visualisation using PCA and t-SNE - unsupervised learning__
- Using an unsupervised learning with PCA and t-SNE to re-cluster the job ads into Data Analyst, Data Scientist, Data Engineer based on the job text

![2d tsne](/99_data/2d_tsne.png)

- 3d visualisation has the advantage of visually being able to inspect the data in space

![3d tsne](/99_data/3d_tsne.jpeg)

## Conclusion:
- Despite being able to classify jobs in the Berlin tech job market into Data Analyst, Data Scientist, Data Engineer after training a SVM model, the accuracy achieved is only based on a manually imputed job classification, that reflects the indecisiveness in the market
- Looking at the unsupervised model confirms the large overlap between jobs in the market.


## Next steps and open items:
- exclude company names from lemmatized text
- focus on pre-defined job requirements to train the models
- run hyperparameter optimization for t-SNE
- run hyperparameter optimization for LDA
- refine the translation into english as there are still some jobs left, that have not been translated properly
- compare the results to other tech job markets like San Francisco or Tel Aviv
