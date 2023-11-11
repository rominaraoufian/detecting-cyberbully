# Detecting CyberBully in tweets
## Data
data that is used in this project is a combination of 4 dataset [labeled tweets](https://github.com/dhavalpotdar/detecting-offensive-language-in-tweets/blob/master/labeled_tweets.csv), [public data labeled](https://github.com/dhavalpotdar/detecting-offensive-language-in-tweets/blob/master/public_data_labeled.csv), [tweeter parsed dataset](https://data.mendeley.com/datasets/jf4pzyvnpj/1), and [cyberbullying tweete](https://www.kaggle.com/datasets/andrewmvd/cyberbullying-classificatio).
the purpose of combining these 4 datasets was to create balanced dataset.
final dataset is devided into 2 classes. (bully, not-bully)
bully types in dataset: age, religion, gender, ethniticy
## Preprocessing
- cleaning data (deleting links and emails, RT, punctuation marks, and spaces,emoji, numbers)
- Common abbreviated structures in English were replaced with their full form
- lowercasing 
- stemming (porter stemmer, snowball stemmer, lancaster stemmer)
- lemmatizing
- TF-IDF
- embedding (Bert, Glove)
- padding (pre, post)

## Models
#### RandomForest

| HyperParameter | values |
| ------ | ------ |
| N_estimators |200, 300, 400, 500 |
| Max_features | Sqrt, log2 |
| Max_depth | 4, 5, 6, 7, 8 |
| Criterion |Gini, entropy |

#### SVM

| HyperParameter | values |
| ------ | ------ |
| C |1, 10 |
| Kernel | linear, rbf, poly, sigmoid |
| Gamma | 0.01, 0.0001 |
| Degree | 4, 6, 8 |

#### BERT

| HyperParameter | values |
| ------ | ------ |
| Model Name |Bert-base-uncased|
| Embedding | BERT Embedding |
| Padding |Pre/Post |
| Batch Size | 16 |
|Epochs|3|
|Max Length|40|
|Learning Rate|2e-7|
|Optimizer|AdamW|

#### RNN

| HyperParameter | values |
| ------ | ------ |
| Embedding |GLOVE|
| Embedding Dim | 100 |
| Padding |Pre/Post |
| Batch Size | 32 |
|Epochs|10|
|Max Length|40|
|Learning Rate|3e-4|
|Optimizer|AdamW|
|DropOut|0.5|
|Hidden Dim|70|
|Loss Function|Binary-cross-entropy|

#### Bi-LSTM

| HyperParameter | values |
| ------ | ------ |
| Embedding |GLOVE|
| Embedding Dim | 100 |
| Padding |Pre/Post |
| Batch Size | 32 |
|Epochs|10|
|Max Length|40|
|Learning Rate|3e-4|
|Optimizer|AdamW|
|DropOut|0.5|
|Hidden Dim|70|
|Loss Function|Binary-cross-entropy|

## Result
#### Best RandomForest
- f1-score: 0.8456
- Max feature: sqrt
- Max depth: 8
- Number of e0stimators: 500
- Criterion: Gini
- Stop word: Delete
- Lower Case: yes
- normalization: Porter stemmer

#### Best SVM
- f1-score : 0.8456
- C: 1
- Kernel: Linear
- Stop word: Delete
- Lower Case: No
- normalization: Porter stemmer

#### Best BERT
- f1-score : 0.8595
- Padding: Pre
- Stop word: Delete
- Lower Case: Yes
- normalization: Lemmatization

#### Best RNN
- f1-score : 0.9324
- Padding: Pre
- Stop word: Delete
- Lower Case: No
- normalization: Porter Stemmer

#### Best Bi-LSTM
- f1-score : 0.9343
- Padding: Pre
- Stop word: Delete
- Lower Case: No
- normalization: Lemmatization

