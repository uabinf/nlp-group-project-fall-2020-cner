
# Named-Entity Recognition Application

This project is to recognize named-entities in Chinese language. There are three types of named entities in the dataset, including person, organization and location.

<img src="https://github.com/uabinf/nlp-group-project-fall-2020-cner/blob/main/image/cner_example.png" width="800"/>

# Models

We implemented this project with two models. One is Bi-LSTM model, and the other is ID-CNNs Model.

Bi-LSTM Model for NER (Named-Entity Recognition):

<img src="https://github.com/uabinf/nlp-group-project-fall-2020-cner/blob/main/image/bi-lstm.png" width="500"/>

<img src="https://github.com/uabinf/nlp-group-project-fall-2020-cner/blob/main/image/bi-lstm%20model.png" width="400"/>

ID-CNNs(Iterated Dilated Convolutional Neural Networks) Model is a faster alternative to Bi-LSTMs for NER: 

<img src="https://github.com/uabinf/nlp-group-project-fall-2020-cner/blob/main/image/id-cnns.png" width="800"/>

# Execution
These commands are only for the UAB Cheaha server (https://docs.uabgrid.uab.edu/wiki/cheaha). <br>
### Connect to Cheaha 
Start your terminal. <br>
Copy/Paste this command in your local terminal to connect to Cheaha. <br>
```
ssh blazerid@cheaha.rc.uab.edu
```

### Clone CNER
Copy/Paste this command in your local terminal to clone this project:
```
git clone https://github.com/uabinf/nlp-group-project-fall-2020-cner.git
```

### UAB Cheaha Sever
There are two methods to run jupyter notebook on UAB Cheaha Sever. <br>
You can choose one of them.<br>
#### 1. Cheaha Dashboard 
(https://rc.uab.edu/pun/sys/dashboard)
```
Interactive Apps -> Jupyter Notebook
```
Then you can see the page as below: <br>
<img src="https://github.com/uabinf/nlp-group-project-fall-2020-cner/blob/main/image/cheaha.png" width="1000"/>
```
Set the papameters as shown above -> Launch -> Connect to Jupyter
```
Copy/Paste this in your Cheaha terminal to ssh to your applied host: <br>
```
ssh c<host_id>
```

#### 2. Cheaha Terminal
Copy/Paste this in your Cheaha terminal to submitted batch job:
```
sbatch ./script/cheaha_job.sh
```
You will get a log file `jupyter-log-pascal-<job_id>.txt`. <br>
Here is an exmaple of the log file: <br>
```
The following have been reloaded with a version change:
  1) CUDA/9.2.148.1 => CUDA/10.1.243



   Copy/Paste this in your local terminal to ssh tunnel with remote  
   ------------------------------------------------------------------
   ssh -L 8349:172.20.201.103:8349 <blazerid>@cheaha.rc.uab.edu           
   ------------------------------------------------------------------


   Then open a browser on your local machine to the following address
   ------------------------------------------------------------------
   localhost:8349                                                
   ------------------------------------------------------------------


/share/apps/rc/software/Anaconda3/5.3.1/lib/python3.7/site-packages/notebook/services/kernels/kernelmanager.py:19: VisibleDeprecationWarning: zmq.eventloop.minitornado is deprecated in pyzmq 14.0 and will be removed.
    Install tornado itself to use zmq with the tornado IOLoop.
    
  from jupyter_client.session import Session
[I 14:35:43.631 NotebookApp] [nb_conda_kernels] enabled, 5 kernels found
[I 14:35:48.993 NotebookApp] JupyterLab extension loaded from /share/apps/rc/software/Anaconda3/5.3.1/lib/python3.7/site-packages/jupyterlab
[I 14:35:48.993 NotebookApp] JupyterLab application directory is /data/rc/apps/rc/software/Anaconda3/5.3.1/share/jupyter/lab
[I 14:35:49.088 NotebookApp] [nb_conda] enabled
[I 14:35:49.088 NotebookApp] Serving notebooks from local directory: /data/user/<blazerid>
[I 14:35:49.088 NotebookApp] The Jupyter Notebook is running at:
[I 14:35:49.088 NotebookApp] http://172.20.201.103:8349/?token=fab72652490fb10b50e798716914dba5127ebde6ec4660f2
[I 14:35:49.089 NotebookApp]  or http://127.0.0.1:8349/?token=fab72652490fb10b50e798716914dba5127ebde6ec4660f2
[I 14:35:49.089 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 14:35:49.126 NotebookApp] 
```

Copy/Paste this in your Cheaha terminal:
```
ssh -L <ip adddress> <your username>@cheaha.rc.uab.edu
```
Copy/Paste this in brower to open jupyter notebook:
```
[I 16:30:27.170 NotebookApp] The Jupyter Notebook is running at:
[I 16:30:27.170 NotebookApp] http://<ip address>/?token=<token_id>
```

### Enviroment setup
Please do not execute the following commands on the Login Node! You are supposed to request a resource from Cheaha, and 'ssh' to the resource nodes!

Copy/Paste this command in your local terminal to load Anaconda module:
```
module load Anaconda3/2020.07
```
Copy/Paste this command in your local terminal to create Environment:
```
conda env create -f environment.yml
```
Copy/Paste this command in your local terminal to check your environment list, after create environment sucessfully. The environment called ```project``` is the environment for this project.
```
conda env list
```

Please use the installed kernal ```project``` to run the project.

# Dataset

Dataset includes 27818 news title, which is from Chinese People's Daily (中国人民日报).<br>
70% samples for training data, 13% samples for evaluation data, 17% samples for testing data.<br>
For each sample, one Chinese character is a token with IOB tagging.

Sample Instance: 
```
[['因', 'O'], ['此', 'O'], ['，', 'O'], ['这', 'O'], ['次', 'O'], ['政', 'O'], ['府', 'O'], ['危', 'O'], ['机', 'O'], ['终', 'O'], ['于', 'O'], ['得', 'O'], ['到', 'O'], ['化', 'O'], ['解', 'O'], ['，', 'O'], ['对', 'O'], ['俄', 'B-LOC'], ['罗', 'I-LOC'], ['斯', 'I-LOC'], ['来', 'O'], ['说', 'O'], ['是', 'O'], ['值', 'O'], ['得', 'O'], ['庆', 'O'], ['幸', 'O'], ['的', 'O'], ['。', 'O']]
```


# Predicted Results
The predicted results are stored in the file ```predict_result.txt``` under the floder ```./dataset/```. <br>
In this file, first column is the chinese characters, second column is the correct tags, and the third column is the predicted tags. <br>
There is an empty line between each sentence.

For example:
```
辽 B-LOC B-LOC
宁 I-LOC I-LOC
南 O O
部 O O
温 O O
泉 O O
众 O O
多 O O
。 O O

大 B-LOC O
庆 I-LOC O
这 O O
一 O O
步 O O
， O O
走 O O
得 O O
好 O O
！ O O

中 B-LOC O
法 B-LOC O
文 O O
化 O O
研 O O
讨 O O
会 O O
今 O O
天 O O
在 O O
京 B-LOC B-LOC
举 O O
行 O O
。 O O
```
The predict results are very good for the entities which contains more than one chinese characters, but not so good for the phrase which only has one character.

# Training Result
For each training epoch, there would generate a training report, which includes the overall accracy, precision, recall, fscore, and the precision, recall, fscore for each entity type (LOC, PRE, ORG). <br>

For example:

Training result for ID-CNNs Model: <br>
<img src="https://github.com/uabinf/nlp-group-project-fall-2020-cner/blob/main/image/training_result.png" width="600"/>

Training result for Bi-LSTM Model: <br>
<img src="https://github.com/uabinf/nlp-group-project-fall-2020-cner/blob/main/image/bestF1_Bi_lstm.png" width="600"/>

# Comparison 
(Cheaha,  NVIDIA Tesla P100 16GB) <br>
<img src="https://github.com/uabinf/nlp-group-project-fall-2020-cner/blob/main/image/comparison.png" width="600"/>

<img src="https://github.com/uabinf/nlp-group-project-fall-2020-cner/blob/main/image/comparison_entity.png" width="400"/>

## Model Parameters

<img src="https://github.com/uabinf/nlp-group-project-fall-2020-cner/blob/main/image/Bi-lstm-hyperp.png" width="800"/>

# Conclusions
Based on the F1 scores obtained by ID-CNNs and Bi-LSTM models, we can tell that these two models work well with Chinese characters. We make a training time comparison between those two models. F1 score: 0.80 is set up as the target. ID-CNNs can achieve the F1 score within 130 seconds. However, Bi-LSTM needs 7272 seconds to achieve the target. 


# Paper Reference
```
[1] Strubell, Emma, et al. "Fast and accurate entity recognition with iterated dilated convolutions." arXiv preprint arXiv:1702.02098 (2017).
[2] Yu, Fisher, and Vladlen Koltun. "Multi-scale context aggregation by dilated convolutions." arXiv preprint arXiv:1511.07122 (2015).
[3] Yoon, Wonjin, et al. "Collabonet: collaboration of deep neural networks for biomedical named entity recognition." BMC bioinformatics 20.10 (2019): 249.
```
