# context-graph
SJSU CMPE 295 Master Project

# To run the Neuralcoref auto generated knowledge graph, please ensure that
1. build Spacy from source (do not use pip install)

python -m pip install -U pip                   # update pip
git clone https://github.com/explosion/spaCy   # clone spaCy
cd spaCy                                       # navigate into directory

python -m venv .env                            # create environment in .env
source .env/bin/activate                       # activate virtual environment
export PYTHONPATH=`pwd`                        # set Python path to spaCy directory
pip install -r requirements.txt                # install all requirements
python setup.py build_ext --inplace  

2. build neuralcoref from source (do not use pip install)
git clone https://github.com/huggingface/neuralcoref.git
cd neuralcoref
pip install -r requirements.txt
pip install -e .

3. python -m spacy download en_core_web_lg
You need to run in Jupyter Notebook with Python 3. Colab doesn't work since it keeps crashing. 



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
