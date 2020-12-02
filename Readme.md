
# Named-Entity Recognition Application

This project is to recognize named-entities in Chinese language. There are three types of named entities in the dataset, including person, organization and location.

<img src="https://github.com/uabinf/nlp-group-project-fall-2020-cner/blob/main/image/cner_example.png" width="800"/>

# Model

Bi-LSTM Model for NER (Named-Entity Recognition):

<img src="https://github.com/uabinf/nlp-group-project-fall-2020-cner/blob/main/image/bi-lstm.png" width="500"/>

ID-CNNs(Iterated Dilated Convolutional Neural Networks) Model is a faster alternative to Bi-LSTMs for NER: 

<img src="https://github.com/uabinf/nlp-group-project-fall-2020-cner/blob/main/image/id-cnns.png" width="800"/>

# Execution
### Clone CNER
Copy/Paste this command in your local terminal to clone this project:
```
git@github.com:uabinf/nlp-group-project-fall-2020-cner.git
```

### Enviroment setup
These commands are only for the UAB Cheaha server (https://docs.uabgrid.uab.edu/wiki/cheaha). <br>
Copy/Paste this command in your local terminal to load Anaconda module:
```
module load Anaconda3/2020.07
```
Copy/Paste this command in your local terminal to create Environment:
```
conda env create -f environment.yml
```

Submit a job on Cheaha server (https://rc.uab.edu/pun/sys/myjobs). <br>
You will get a log file `/jupyter-log-pascal-<log_id>.txt`. <br>
These commands can be found  in the log file to run jupyter notebook on Cheaha. <br>

Copy/Paste this in your local terminal to ssh tunnel with remote:
```
ssh -L <ip adddress> <your username>@cheaha.rc.uab.edu
```
Copy/Paste this in brower to open jupyter notebook:
```
[I 16:30:27.170 NotebookApp] The Jupyter Notebook is running at:
[I 16:30:27.170 NotebookApp] http://<ip address>/?token=<token_id>
```


# Dataset

Dataset includes 27818 news title, which is from Chinese People's Daily (中国人民日报).<br>
70% samples for training data, 13% samples for evaluation data, 17% samples for testing data.<br>
For each sample, one Chinese character is a token with IOB tagging.

Sample Instance: 
```
[['因', 'O'], ['此', 'O'], ['，', 'O'], ['这', 'O'], ['次', 'O'], ['政', 'O'], ['府', 'O'], ['危', 'O'], ['机', 'O'], ['终', 'O'], ['于', 'O'], ['得', 'O'], ['到', 'O'], ['化', 'O'], ['解', 'O'], ['，', 'O'], ['对', 'O'], ['俄', 'B-LOC'], ['罗', 'I-LOC'], ['斯', 'I-LOC'], ['来', 'O'], ['说', 'O'], ['是', 'O'], ['值', 'O'], ['得', 'O'], ['庆', 'O'], ['幸', 'O'], ['的', 'O'], ['。', 'O']]
```


## On going
Still working on the Feature Work mentioned in the poster section. One model is under training process. The model will be uploaded very soon.    




