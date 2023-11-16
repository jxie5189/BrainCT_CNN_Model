# BrainCT_CNN_Model
An neural network assignment from Machine Learning using Convolutional Neural Network 

Dataset: https://www.kaggle.com/code/metamadyeth/ml-project-image-classification

Original code from Google colab, the **code assumes that the dataset is already in the google drive**. The notebook makes a connection to the google drive and extracts the dataset. Data processing techniques are also referenced in the code as many other have worked on this dataset. The dataset is convert into a DataFame with the path of each sample under 'Path' column and 'label' as the label of each images. 

Method processImage pads the image if the input image's size is not (512,512). The Convolutional Neural Network (CNN) used originally contains 3 convo layers, but 2 convo layers were also able to produce an accuracy of >98% in epochs of 3. No validation testing was done, data set was split into training and testing, with test size of 0.2. You may uncomment out the extra convo layer with 128 neurons and change the epochs to 5. 

The model is compiled using the 'categorical_crossentropy', because the output layer would have 3 classes and each class would be assigned a probability. Similary, the label (y valuable) is converted to categorical data. 

The model's output is then processed via the model_translate method. The method uses a labelmap (previously defined when converting labels into numerical value), and normalizes the output probability in the range of 0 to 1. The labels and normalized probabilities are convert into a DataFrame for easier manipulation to determine the highest percentage, and predicted class of the highest percentage. 

The application object, NeuroCTScanner, only have 4 methods. The loadModel takes the CNN that we previously establish and assigns it to the object's model. The displayImage and \__convert_image__ are technically both helper methods to evaluateImage. When evaluateImage is called, the parameter is sent to the \__convert_image__ method and processes it by resizing (if necessary) and converting to an array format. The ready image is then fed into the CNN model and the result is fed into model_translate method from earlier. In sum, the evaluateImage method is a combination of processImage, CNN, and displayImage methods. 

The application object is randomly tests with 3 samples from the the test set and calls the evaluateImage method to display the image of the brain CT, the highest percentage and predicted class, and a summary of of other class and their probability. 
