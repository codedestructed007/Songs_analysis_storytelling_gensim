# Songs Analysis with Genre Prediction 🎵

This project dives into the fascinating world of music genres through Natural Language Processing (NLP) techniques. We explore how text data associated with songs can help us understand and predict their genres using the Doc2Vec model from the Gensim library.

## Overview 📊

Understanding music genres is a complex yet intriguing task. Here, we've harnessed the power of NLP to delve into song lyrics and associated textual data to decode and predict genres. By leveraging various NLP techniques, we've extracted insightful features and patterns that define different musical categories.

## Techniques & Libraries Used 🛠️

- **NLP Filtering:** Leveraged advanced NLP techniques as filters to process song lyrics and extract meaningful insights related to genres.
- **Doc2Vec Model (Gensim):** Utilized the Doc2Vec algorithm from the Gensim library to create embeddings for song text data and predict genres based on these embeddings.

## How to Use 🚀

1. **Data Preprocessing:** Ensure song data is in a suitable format for analysis.
2. **NLP Filtering:** Apply NLP techniques to preprocess and filter the text data associated with songs.
3. **Doc2Vec Model:** Utilize Gensim's Doc2Vec library to create embeddings and predict genres for songs.

## Example Usage 💡

```python

# Import necessary libraries
from gensim.models.doc2vec import Doc2Vec, TaggedDocument

# Define the function to train the Doc2Vec model
def word_to_vec(input_list, output_list, vector_size=150, min_count=5, epochs=40):
    tagged_data = [TaggedDocument(words=input_column, tags=[output_column]) for input_column, output_column in zip(input_list, output_list)]
    model = Doc2Vec(vector_size=vector_size, min_count=min_count, epochs=epochs)
    model.build_vocab(tagged_data)
    model.train(tagged_data, total_examples=model.corpus_count, epochs=model.epochs)
    return model

model = word_to_vec(X_list,y_list,vector_size=8000,epochs=30)

def Predict_genre(model,text):
    text_vector = infer_vector(model, text)
    return model.dv.most_similar([text_vector],topn = 1)[0][0]

text = "How many roads must a man walk down Before you call him a man? How many seas must a white dove sail Before she sleeps in the sand? Yes, and how many times must the cannonballs fly Before they're forever banned?"
Predict_genre(model,text)
'pop'


