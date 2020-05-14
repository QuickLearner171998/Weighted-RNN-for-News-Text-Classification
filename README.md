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