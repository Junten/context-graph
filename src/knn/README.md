## KNN Topic Classification
**SJSU CMPE 295 Master Project - (Context Graph) Group**

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

## Google Colab Notebook Link
https://colab.research.google.com/drive/1KKGNYr6HtdLNMkcIAr3-pGPTw26U1-ok
