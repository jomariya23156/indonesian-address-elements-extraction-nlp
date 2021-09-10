# Indonesian Address Elements Extraction with NLP
## Overview
This is our team DayBuilder's works from Data Science competition from Shopee Code League 2021.  
The main competition page and problem statement can be found on Kaggle: https://www.kaggle.com/c/scl-2021-ds  
**All trained models are available here: https://drive.google.com/file/d/1IaDkMDyXvPXVl3buq4SjQkFZksQSKniC/view?usp=sharing**  

## Result  
**Final result:** The best model achieved **59.62%** accuracy on Test set ranked **117th** from **1,034** teams (Top 12%).   

## All Models performance
- Model 1 (xx_ent_wiki_sm model with nlp.initialize()) Test Accuracy: **58.60%**  
- Model 2 (en_core_web_large model) Test accuracy: **51.22%**  
- Model 3 (xx_ent_wiki_sm model without nlp.initialize()) Test Accuracy: **57.90%**  
- Model 4 (using Model 1 with better-preprocessed training data and Train longer) Test accuracy: **59.62%** (Best)  

## Our approach
We use **Named Entity Recognition (NER)** NLP model to solve this problem. At first, we want to try Seq2Seq model but luckily we've found a post on discussion on the Kaggle that Seq2Seq perfroms badly. So, we go for NER. Instead of training the model from scratch, we dicided to use the pre-trained models from spaCy and continue training from there. Practically, this might give a better result. Then, we preprocess the data to match the training data format for spaCy and feed it into training.  

## What we've done
- Explore the data
- Clean and Prepare the data for training with deepparse
- Train with deepparse (failure occurred by some errors)
- Clean and Prepare the data for training with spaCy
- Train with spaCy
- Hyperparameter tuning
- Try other models

## Problems we've found
- Errors occurred during training with deepparse model (Later, we've found that it occurred because there are some double space in the raw address, so after we've splitted by space, it gave an extra space token which we have not labelled it for training. This leads to input dimensional mismatch on PyTorch which deepparse is built on.)  
- Cannot solve the incomplete raw address (We tried many different methods but none of them work. You can refer the file "Explore_incomplete_address.ipynb" for more detail about our experiment.)
