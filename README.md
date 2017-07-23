# Query Based Abstractive Summarization
## Overview 
Implementation of diversity based attention model for query based abstractive summarization task. The implementation is adapted from the seq2seq package in Tensorflow.

The implementation is based on [this](https://arxiv.org/abs/1704.08300) work.
> Diversity based attention models for Query based abstractive summarization

> Preksha Nema, Mitesh M. Khapra, Anirban Laha, Balaraman Ravindran

> ACL, 2017

## Requirements:
* [tensorflow-0.12](https://www.tensorflow.org/versions/r0.12/get_started/os_setup)
* [gensim](https://pypi.python.org/pypi/gensim)
* [nltk](http://www.nltk.org/install.html)

## Data Download and Preprocessing
    * cd src/dataextraction_scripts
    * The model will extract the data for the categories mentioned in file debatepedia_categories
    * sh extract_data.sh

## Get the Glove embeddings:
    wget http://nlp.stanford.edu/data/glove.840B.300d.zip
    mkdir Embedding
    mv glove.840B.300d.zip Embedding
    unzip glove.840B.300d.zip
 
 ## Configuration file:
     * The hyper parameters could be changed in the config.txt file.
     * The influence of eah hyperarameter have been explained in detail in the comments in config.txt
 ## Train the model
      sh ./train.sh config.txt
      
 ## Inference:
     test.sh will refer to the config.txt to initialize the graph that will be used for creating the graph for inference.
     sh ./test.sh config.txt

## Evaluation:
    The test.sh script will generate the predictions for the test data in the working directory output directory mentioned
    in the config.txt file.
    python eval.py --output_dir output/test_final_results_plabels data/test_content
