# Weighted-RNN-for-News-Text-Classification
Implementation of https://arxiv.org/ftp/arxiv/papers/1909/1909.13077.pdf

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
### Overall statistics
| Model | Test Accuracy | Macro avg. precision | Macro avg. recall | Macro avg. F1 | Avg. time/epoch | Convergence rate |
| ----- | ------------- | -------------------- | ----------------- | ------------- | --------------- | ---------------- |
| WRNN (GRU unit) | 85.73 | 86.0 | 85.0 | 85.0 | 40.02 | 7 |
| WRNN (LSTM unit) | 87.37 | 88.0 | 87.0 | 87.0 | 34.23 | 9 |
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
