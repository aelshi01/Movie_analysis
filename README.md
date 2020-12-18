# Movie_analysis
## Gather Data

1) The data gathered is the one as suggested by the Feedstock team
2) Kaggle – imdb dataset in pandas data frame

## Explore data

I have analysed the data using Keras and TensorFlow.

I will be using the following metrics to be able to make sense of our data:

1.	Number of samples: Total number of examples you have in the data.
2.	Number of classes: Total number of topics or categories in the data.
3.	Number of samples per class: Number of samples per class (topic/category). In a balanced dataset, all classes will have a similar number of samples; in an imbalanced dataset, the number of samples in each class will vary widely.
4.	Number of words per sample: Median number of words in one sample.
5.	Frequency distribution of words: Distribution showing the frequency (number of occurrences) of each word in the dataset.
6.	Distribution of sample length: Distribution showing the number of words per sample in the dataset.


## Model

At this stage before looking into preprocessing it is important to establish a heuristic for picking our model and deciding what we need from our data before doing some preprocessing.

Having explored the data and covered some literature on the topic, I have for simplicity broken it down to two models.  The first is a sequence model, which if chosen I would go for a basic CNN.  The second and most probable to use is a n-gram model – text is seeing as sets of words and for this I would use a multi-layer perceptron.  Having done some exploratory data analysis and found in the paper [2] written by Aitziber Atutxa , Kepa Bengoetxea ,Arantza Diaz de Ilarraza ,Mikel Iruskieta that the number of  samples to the number of words per sample is correlated with model performance.  

Thus, due to our ratio approximately 144 I will be using a MLP to build our classifier.

## Prepare data

To prepare the data I will be splitting the training data into an extra dataset for validation.  The idea is to make sure our classifier does not overfit the training data and to increase higher accuracy in the test data results.  I will be splitting the training set and validation set into 80/20, respectively as is common to do.  Also the data we have may be ordered in a specific way and we do not want that to influence our outcome, and therefore need to randomise the ordering of our sample.  

In addition, having decided to use MLP for our model we know that machine learning algorithms need numbers as input to compute and find relationships.  Therefore, we must convert letters and words into numbers and then find a way to measure semantics and relationship between words.

To do this I will be doing the following two process on the dataset:

1.	Tokenisation
2.	Vectorisation

Lastly, for the preprocessing phase I will then perform some feature selection to optimize for performance. 





## Build, Train and evaluate model

As mentioned above I will be using MLP to train our model on the binary classification problem we are trying to solve for.  For the MLP I will be constructing is two layers, which will be tested and accordingly I can adjust my results.

Another consideration will be the dropout layers, which helps with reducing overfitting of the data and a common practice for optimal results.  Also, the chosen loss function that is used to adjust the error in the model is the binary cross-entropy. Lastly, for the last layer aka activation layer I will be using sigmoid function to reduce a binary classification into a single digit score of probability (between 0 and 1).  



## Tune Hyperparameters

A good method to use is the GridSearchCV function for hyperparameter tuning, which allows you to try multiple values all at once.  Due to time constraints, I have not implemented this at the moment but will do so in the future.

## Deploy model

On the cloud, using something like the AI platform offered by google, which makes deploying ML models at a cost-effective and efficient process.

TensorFlow was developed for production and it provides a solution for model deployment - TensorFlow Serving. Basically, there are three steps:

1.	Export your model for serving
2.	Create a Docker container with your model 
3.	Deploy it with Kubernetes into a cloud platform, i.e. Google Cloud or Amazon AWS.

The first two step is done locally for testing and iterative improvements.  The last stage is when we transfer it from local to public by hosting it in the cloud.
