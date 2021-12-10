# NLP_DisasterTweets_Kaggle_Comp
NLP Kaggle Competition (Disaster Tweets) 

# Objective

The objective of this project is to classify tweets according to two classes: are the sequences of text talking about a real natural disaster or not? It is part of a Kaggle competition that can be found here: https://www.kaggle.com/c/nlp-getting-started

# Environment and tools

To implement my solution, I will use the HuggingFace/TensorFlow frameworks and more specifically I will fine-tune a DistilBERT type of Transformer. DistilBERT is a small, fast, cheap and light Transformer model trained by distilling BERT base. It has 40% less parameters than bert-base-uncased, runs 60% faster while preserving over 95% of BERT’s performances as measured on the GLUE language understanding benchmark.


# Project steps

	1. Inspect and prepare the data

The input data comes as a CSV file containing 7613 tweets, labeled 1 or 0 (real natural disaster or not). Firstly, I tokenize all sequences of text using the appropriate Tokenizer for DistilBERT: DistilBertTokenizerFast. Then I split the dataset of sequences of tokens into training and validation sets. Both datasets are finally converted to tf.data.Dataset format for ingestion.

	2. Train
	
The pre-trained model is compiled with an AdamWeightDecay optimizer and then trains on batches of 16 sequences over 1 epoch, reaching approximately 82% on our validation set.

	3. Classify
	
The test set comes in a CSV file of unlabeled tweets that need to be pre-processed the same way: tokenize all sequences of text, than call the predict() method to output the probability for each class (0 or 1). And finally use the argmax() function to assign the final label.
  
  	4. Conclusion & Submission on Kaggle

Transformers tend to overfit very quickly, therefore 1 epoch was enough to achieve good performance and label all rows of the CSV test file for submission. Kaggle has an automated system that evaluates scores and ranks submissions. As of today, this project ranks #152 over 952 participants.
