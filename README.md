# Image-Captioning-RNN
Image Captioning using Recurrent Neural Networks on Flickr images with pretrained ResNet50 model features.

![result](/output.png)

## Data Documentation
A new benchmark collection for sentence-based image description and search, consisting of 8,000 images that are each paired with five different captions which provide clear descriptions of the salient entities and events. … The images were chosen from six different Flickr groups, and tend not to contain any well-known people or locations, but were manually selected to depict a variety of scenes and situations. For more information please read the [data documentation](https://www.kaggle.com/datasets/adityajn105/flickr8k).

## Code Explanation

- **Import Libaries and Dataset**: The code imports the necessary libraries such as TensorFlow, Keras, sklearn, etc. and downloads the Flickr8k dataset that contains images and captions.
- **Creating Features and Captions Dictionary**: The code uses a pretrained ResNet50 model to extract features from each image and stores them in a dictionary with the image ID as the key. It also reads the captions file and creates another dictionary with the image ID as the key and a list of captions as the value.
- **Preprocessing and Tokenizing**: The code cleans the captions text by converting to lowercase, removing punctuation, adding start and end tokens, etc. It also creates a tokenizer object that maps each word to an integer index and finds the maximum length of captions for padding.
- **Data Generator**: The code defines a data generator function that yields batches of input and output pairs for training the model. For each image and caption, it creates multiple samples by splitting the caption into partial sequences and encoding them using the tokenizer.
- **Model**: The code defines the image captioning model using Keras functional API. It consists of an encoder model that takes the image features and a sequence feature layer that takes the caption sequence as inputs, and a decoder model that combines them and produces a softmax output over the vocabulary size.

![architecture](/architecture.png)

- **Train**: The code splits the data into train and test sets, creates a data generator for the train set, and trains the model for 20 epochs using categorical crossentropy loss and Adam optimizer.
- **Test**: The code loads the trained model and defines a function to generate captions for new images. It randomly selects some images from the test set, displays them, and shows the predicted captions along with the real captions and their similarity scores using BERT embeddings.


