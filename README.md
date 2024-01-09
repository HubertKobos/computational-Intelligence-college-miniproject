# 1. Introduction 
The assumption of the project was to create three convolutional neural networks with different architectures to recognize images of vegetables and compare them. The dataset used for training is Vegetable Image Dataset from Kaggle.com: https://www.kaggle.com/datasets/misrakahmed/vegetable-image-dataset. Dataset contains 15 types of common vegetables. The vegetables are:
*	Bean
*	Bitter
*	Gourd
*	Bottle gourd
*	Brinjal
*	Broccoli
*	Cabbage
*	Capsicum
*	Carrot
*	Cauliflower
*	Cucumber
*	Papaya
*	Potato
*	Pumpkin
*	Radish
*	Tomato
A total of 21000 images from 15 classes are used where each class contains 1400 images of size 224x224 and in .jpg format. The dataset split 70% for training, 15% for validation and 15% for testing purpose.

# 2. Solution
## 2.1 Analysis of dataset
To analyze the structure of files I created the following loop to display the number of file contents in each subdirectory of the main data directory.
#####
![](https://i.imgur.com/2zP8i0x.png)
#####
To check the number of classes and if in each directory (test, validation, train) was exactly the same amount of classes contained, I created script to sum up the classes and return their names.
#####
![](https://i.imgur.com/RjpYeTT.png)
#####
To get to know the dataset better I created a function that renders x random images from the dataset with it filename, type name and the sub dataset name.
#####
![](https://i.imgur.com/BI3bFA6.png)

## 2.2.	Preparation of dataset for training
ImageDataGenerator class was used to rescale matrix values, each image pixel values are divided by 255 which is the maximum value of the pixel. Ultimately, I wanted to obtain values between 0 and 1. Additionally, I divided the data into segments of 32 (batches).
#####
![](https://i.imgur.com/gx5XtXd.png)
## 2.3.	Designing first neural network
First designed architecture will be a reference for second and third neural network. I decided to make It simple.
#####
![](https://i.imgur.com/P9MIgYS.png)
#####
Model was trained for  5 epochs
#####
![](https://i.imgur.com/pZmucb3.png)
#####
To visualize validation loss and validation accuracy the plot_histories() function was created
#####
![](https://i.imgur.com/YaVjtsx.png)
#####
As can be seen in the history diagrams, model is improving during training. The training accuracy is increasing and the training loss is decreasing, which indicates that the model is learning from the data.
#####
![](https://i.imgur.com/DZqOlWB.png)
## 2.4.	Designing second neural network
The second neural network architecture is the same as baseline_model architecture but without two Conv2D layers. The architecture is simpler than the previous one. Same activation functions were used.
#####
![](https://i.imgur.com/fsepvrg.png)
#####
Results of training shows that the second model improved, it achieves better training and validation accuracy across all epochs. The validation accuracy of the improved model is consistently higher, suggesting better generalization to unseen data. The training loss is decreasing, indicating that the models are learning from the training data. The improved model has a higher overall accuracy, which is a positive sign.
#####
![](https://i.imgur.com/EgiVEBx.png)
## 2.5.	Designing third neural network
The third neural network architecture differs from the others in the activation functions, number of neurons and output layers. I decided to use Tanh and Elu activate functions. 
Tanh is a symmetric around zero which helps to center the data. It eliminates “dead neurons”, which might be the problem of ReLU. It return values in the range of (-1, 1).
ELU tries to solve “dead neurons” by creating negative values. It can improve model generalization ability, especially in classification problems.
#####
![](https://i.imgur.com/h2w6eDf.png)
##### 
As we can see on the histories diagram the third model has the highest accuracy during first epochs. On the 3. and 4. epoch it has similar result as model_1. The third model also has the highest training accuracy from the very begging which is desirable. It started to have the lowest train_loss from the begging of the training but on the 3. and 4. epoch the results were similar to model_1 train_loss. Validation_loss was the lowest from the begging of the training comparing to baseline_model and model_1. 
#####
![](https://i.imgur.com/Gw8Szqr.png)
# 3.Summary 
The project presented three different architectures of CNNs. Could be observed that first two models results were relatively similar to each other, but the third was much better from the very beginning of training process. There are many factors that can influence why certain models perform better compared to others. The difference in the model_3 training process compared to the previous two models might be because it has different activation functions (tanh, elu) which might help in capturing various aspects of data, especially when data contains various features. Model_3 uses different number of filters and Pooling layers, which helps in more diverse analysis of images at different scales.
