
# Named-Entity Recognition Application

This project is to recognize named-entities in Chinese language. There are three types of named entities in the dataset, including person, organization and location.



# Model

This model is Iterated Dilated Convolutional Neural Networks with a Conditional Random Field layer, which is proposed in the paper [Fast and Accurate Entity Recognition with Iterated Dilated Convolutions](https://arxiv.org/abs/1702.02098). In the paper, the authors proposed a faster alternative to Bi-LSTMs for NER (Named-Entity Recognition): Iterated Dilated Convolutional Neural Networks, which has better capacity than traditional CNNs for large context and structured prediction. It permits fixed-depth convolutions to run in parallel across entire documents. It enables dramatic 14-20x test time speedups while retaining accuracy comparable to the Bi-LSTM-CRF. Moreover, the proposed model trained to aggregate context from the entire document are even more accurate while maintaining 8x faster test time speeds.

The linear chain CRF (Conditional Random Field) is used to overcome label-bias problem.

# Dataset

The dataset is from People's Daily (中国人民日版) with IOB(In-Out-Begin) tagging.
This dataset includes 27818 lines in total.

For example: 
"在北京市海淀区魏公村附近，有一家由一对侗族夫妻经营的餐馆。" (Translation: Near Weigong Village in Haidian District, Beijing, there is a restaurant run by a Dong couple.)

在 O <br>
北 B-LOC <br>
京 I-LOC <br>
市 I-LOC <br>
海 B-LOC <br>
淀 I-LOC <br>
区 I-LOC <br>
魏 B-LOC <br>
公 I-LOC <br>
村 I-LOC <br>
附 O <br>
近 O <br>
， O <br>
有 O <br>
一 O <br>
家 O <br>
由 O <br>
一 O <br>
对 O <br>
侗 O <br>
族 O <br>
夫 O <br>
妻 O <br>
经 O <br>
营 O <br>
的 O <br>
餐 O <br>
馆 O <br>
。 O <br>

## Requirement
To set up the enviroment, please use the command:
**pip install -r requirement.txt**


