# German BERT for eBay Machine Learning Challenge

Welcome to the repository detailing my approach for the eBay machine learning competition, specifically tailored for predicting named entities in German text.

## Approach

I have adopted a "pre-train then fine-tune" methodology utilizing BERT models:

#### Pre-train
Initiate the pre-training of the German BERT model by predicting 15% masked words in product listing titles.

#### Fine-tune
Subsequently fine-tune the pre-trained model using the provided named entity labeled data.

## Why 15% Masking for Pre-training?

The choice of a 15% masking rate during pre-training is grounded in several considerations:

- **Robust Training:** The rate is set high enough to robustly train the model on context-based word prediction.

- **Context Retention:** The rate is deliberately kept low to retain sufficient context around the masked words, preserving overall sentence fluency.

- **Research-backed Choice:** Based on research from the original BERT paper, which tested masking rates of 10%, 15%, 20%, and 30%, the 15% masking rate achieved the best downstream task performance after fine-tuning.

## Next Word Prediction

The methodology involves randomly masking 15% of input tokens and training the model to predict the original masked words. This process helps the model learn contextual relationships between words, gaining domain knowledge about terminology specific to eBay listings.

For instance, the model may learn that terms like "sneakers" often follow words like "Nike" or "Adidas," thereby understanding product names and classifications.

## Model Ensemble

In the model ensemble, I utilized three distinct models to enhance named entity predictions:

- **Gelectra-Large:** A large German electra model.
- **GBERT-Large:** A large German BERT model.
- **Regular German BERT:** A standard German BERT model.

This ensemble strategy aims to leverage the unique strengths of each model, enhancing the overall predictive performance.

## Contents

The key files in this repository include:

- `german-bert-model.ipynb`: Jupyter notebook for fine-tuning on the named entity dataset.
- `ensemble.ipynb`: Jupyter notebook for ensembling fine-tuned models to enhance predictions.

