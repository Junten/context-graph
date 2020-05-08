# Deep Context Graph for Actionable Business Decision
SJSU CMPE 295 Master Project

Team Members: 
- Jia Ma
- Kevin Lai
- Ying Laura Liu
- Junteng Tan


![alt text](https://raw.githubusercontent.com/Junten/context-graph/master/images/poster.png?token=ABVFY24IXIZ4BLK5CN6M62S6X34KG)


## ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)KNN Topic Classification



### Background
* **K-nearest neighbors (KNN)** is a machine learning algorithm that is able to perform classification of an object based on the distance between the object and its nearest neighbors.

### Reasoning
* In order to achieve our project's goal, we needed to **construct a timeline** consisting of news articles that would **form the context** of our **knowledge graph**. However, because we have a variety of news articles that focus on different aspects of a subject, we needed to figure out a method to **group closely related news articles together**.
  * For example, during the coronavirus **(COVID-19)** pandemic, many news articles spoke about the different aspects of the pandemic such as the following:
    * **Infection Rate and Death Rate**
    * **Virulence of the Disease**
    * **Availability or Shortage of Medical Supplies and Equipment**
    * **Promising or Potential Treatments and Cures**
    * **Governments' Responses to the Virus around the World**
    * **Lockdown Rules and Impacts**
    * **Etc.**
  * We can see that even when the subject (COVID-19) is the same across multiple news articles, the underlying topics in regards to that subject may actually be different and focus on different aspects of that subject.
* So, because the focus was on classifying objects by **finding other "closely related" objects**, we chose **KNN** because it can **classify an object based on its "closely related" nearest neighbors**.

### Methodology
1. **Get the news article data**
  * We would either fetch recently published news articles from the Internet or use existing news articles from our database as the sample for the KNN training and testing.
2. **Perform Data Cleaning and Preparations**
  * We performed data cleaning and data preparations to convert the contents of the news documents into tokens that form the bag of words that would later be used for topic modeling.
3. **Perform LDA Topic Modeling on the Cleaned data**
  * We performed LDA topic modeling on the resulting bag of words to establish a set of topics that we will classify brand new articles into.
4. **Perform KNN Classification on a New Sample of News Articles**
  * We partitioned our dataset of recently published news articles into an 80/20 split for training and testing.
  * Then, we ran the KNN algorithm on the partitioned dataset to test the KNN's accuracy in classifying news articles.
5. **Check KNN's Prediction Results**
  * We achieved around 60% accuracy with our KNN model when trying to predict the topic of a news article.

### Run Environment
1. **The python notebook was executed and ran on Google Colab.**
  * You do not need to install anything locally when running the code on Google Colab.
  * The code already contains the necessary commands to install the required libraries.

### Google Colab Notebook Link
https://colab.research.google.com/drive/1KKGNYr6HtdLNMkcIAr3-pGPTw26U1-ok


## ![#c5f015](https://via.placeholder.com/15/c5f015/000000?text=+) Polynomial Equation
To be added 

## ![#1589F0](https://via.placeholder.com/15/1589F0/000000?text=+) Stella Graph Link Prediction
This is a graph embedding neural network to predic a future topic. 

1.install required packages
```
pip install tweet-preprocessor
pip install google-api-python-client
pip install -q stellargraph[demos]==1.0.0rc1
```

2.Runtime Environment: Colab GPU enabled 

3.Training Plot

<img width="559" alt="plot" src="https://user-images.githubusercontent.com/47645194/81371569-138d7100-90ad-11ea-8435-8b0c675e2b50.png">


## ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+)Ampligraph 
This is a graph embedding neural network to validate the topic predicted from Stella Graph above.

### steps to run the neuralcoref auto generated knowledge graph
(**do not use pip install. we want to use the latest Spacy version in the later part of the code. But Neuralcoref 4.0 is not compatible with Spacy's 'pip install' version. We have to build from source for both Spacy and Neuralcoref to execute this code in Jupyter Notebook with Python 3.Colab doesn't work since it keeps crashing with Spay and Neuralcoref together.**)

1. build Spacy from source 
https://spacy.io/usage has instruction on how to build spacy from source. 

```
python -m pip install -U pip                   
git clone https://github.com/explosion/spaCy   
cd spaCy                                       
python -m venv .env                            
source .env/bin/activate                      
export PYTHONPATH=`pwd`                       
pip install -r requirements.txt               
python setup.py build_ext --inplace  
```

2. build neuralcoref from source (do not use pip install)
```
git clone https://github.com/huggingface/neuralcoref.git
cd neuralcoref
pip install -r requirements.txt
pip install -e .
```
3. in terminal: 
```
python -m spacy download en_core_web_lg
pip install wikipediaapi
```

4. remove below two lines of code from file. We used these two lines to avoid scraping web time by saving the scraped data to a csv file first. Then you could scrape data yourself! 
pd.read_csv("test1.csv").head()
wiki_data = pd.read_csv("test1.csv")



# ![#c5f015](https://via.placeholder.com/15/c5f015/000000?text=+) Overall Summary

## Deep Context Graph Project Methodoglogy: 
1. Gather text data from news sources
2. Perform Named Entity Recognition (NER) with Spacy on the news text data to get a set of entities
3. Filter the set of entities to obtain a smaller subset containing only interesting and relevant entities: (using entity_type such as Companies and part_of_speech such as Nouns, Adjectives, or a combination of both).
4. Use LDA to Extract Topics from the entity subset
5. Get a list of top related words (based on word frequency) from the topics
6. Perform Google search on each Entity
7. Go to each search results URLs
8. Then, scape text from the URLs
9. Repeat starting from step 2 from above
9a. Create a graph based on the results. (This is the topic graph.)
(Steps in Forming the Context of the Graph)
10. Create/Establish an event timeline with the topic graph using timestamps such as dates/time from the articles. (This timeline will form the context of the graph.)
11. Based on the established event timeline (containing past and present events), predict new events that might occur.
11a. To predict the new events, start by performing distillation (with LSTM or Transformer) on the event timeline
11b. Then, create a deep learning model such as a Neural Network model to predict future events 

## Colabe Links for collaboration 
https://colab.research.google.com/drive/1ORptuFuArk0tqwhZgX7vPgGKtOL1SZpD?authuser=1 (Data scraping)

https://colab.research.google.com/drive/1tlbxxwPYTQZza5yoyFauF-9RPoBMbTlj?authuser=1 (Data scraping)



