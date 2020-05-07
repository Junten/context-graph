# context-graph
SJSU CMPE 295 Master Project

### KNN

### Polynorminal Equation


### Topic Predictor 



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



# Steps to follow: 
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

# Colabe Links for collaboration 
https://colab.research.google.com/drive/1ORptuFuArk0tqwhZgX7vPgGKtOL1SZpD?authuser=1

https://colab.research.google.com/drive/1tlbxxwPYTQZza5yoyFauF-9RPoBMbTlj?authuser=1
