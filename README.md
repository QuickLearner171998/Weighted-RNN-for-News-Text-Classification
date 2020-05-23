# Weighted RNN for News Text Classification
* This repository contains an implementation of https://arxiv.org/ftp/arxiv/papers/1909/1909.13077.pdf
* The task is to classify news articles into one of the 20 categories. Therefore, it is a sentence classification task.

## Architecture details
The following diagram illustrates the architecture of WRNN:
![alt-text](/images/wrnn.png "WRNN")
* Here, wi's are **scalars** which are multiplied with RNN outputs to form a weighted representation.
* The weighted vectors are summed and passed onto fully-connected layers for classification.
* Dropout is added to both after RNN and fully-connected layer 1.
* L2 regularization is employed for the fully-connected layer 1 weights.

## Experimental details
* We used the dataset provided by sklearn library (via the ```fetch_20newsgroups``` function).
* We download the whole dataset and randomly split it into 90:10 train-test partition (random seed is set in code).
* The most frequent **40439** (vocab size mentioned in paper) words are selected for the vocabulary. The pre-trained embeddings are allowed to be fine-tuned during the model training process.
* The paper used 200d word2vec embeddings, but the source is not mentioned. Instead, we use 300d GloVe embeddings and report results using them. We also trained custom 200d word2vec embeddings on the news classification dataset but it overfitted the models.
* SL (max sentence length) is set as **300**.
* From the train partition, 5% of the dataset is used as validation set to select hyperparamters.
* Adam optimizer with early stopping is used to optimize the network weights.

## Use
* Download the **WRNN_News_Text_Classification.ipynb** file.
* Add the above file to your Google Drive.
* Make a folder with name **nnfl_project** in your drive.
* Download these [GloVe](http://nlp.stanford.edu/data/glove.840B.300d.zip) embeddings directly in your Drive. Run the following commands in a cell of the notebook after mounting your Drive (1st cell in the notebook):
```
!wget -P /content/drive/My\ Drive/ http://nlp.stanford.edu/data/glove.840B.300d.zip
!unzip /content/drive/My\ Drive/glove.840B.300d.zip -d /content/drive/My\ Drive/
```
* Now, you should have the GloVe embeddings in your Google Drive. Make sure they are **not** inside any folder.
* Next, run all the cells after the first cell and excluding the GloVe download cell.

## Results
* We report results on the test set for WRNN (with GRU unit), WRNN (with LSTM unit), GRU baseline and BiGRU baseline models.
* The results are left as such in the notebook file above.

### Overall statistics
| Model | Test Accuracy | Macro avg. precision | Macro avg. recall | Macro avg. F1 | Avg. time/epoch | Convergence rate |
| ----- | ------------- | -------------------- | ----------------- | ------------- | --------------- | ---------------- |
| WRNN (GRU unit) | 85.73 | 86.0 | 85.0 | 85.0 | 40.02 | 7 |
| WRNN (LSTM unit) | 87.69 | 88.0 | 87.0 | 87.0 | 34.99 | 11 |
| GRU baseline | 81.37 | 82.0 | 80.0 | 81.0 | 41.31 | 3 |
| BiGRU baseline | 77.88 | 79.0 | 77.0 | 78.0 | 75.66 | 3 |
### WRNN (GRU unit) Statistics
#### Graphs
![](/images/wrnn_gru_acc.png) ![](/images/wrnn_gru_loss.png)
#### Confusion Matrix
![](/images/wrnn_gru_cf.png)
#### Classification Report
![](/images/wrnn_gru_clf.PNG)

### WRNN (LSTM unit) Statistics
#### Graphs
![](/images/wrnn_lstm_acc.png) ![](/images/wrnn_lstm_loss.png)
#### Confusion Matrix
![](/images/wrnn_lstm_cf.png)
#### Classification Report
![](/images/wrnn_lstm_clf.PNG)

### GRU baseline Statistics
#### Graphs
![](/images/gru_acc.png) ![](/images/gru_loss.png)
#### Confusion Matrix
![](/images/gru_cf.png)
#### Classification Report
![](/images/gru_clf.png)

### BiGRU baseline Statistics
#### Graphs
![](/images/bigru_acc.png) ![](/images/bigru_loss.png)
#### Confusion Matrix
![](/images/bigru_cf.png)
#### Classification Report
![](/images/bigru_clf.PNG)
