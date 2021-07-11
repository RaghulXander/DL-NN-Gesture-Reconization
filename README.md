# DL-NN-Gesture-Reconization

Imagine you are working as a data scientist at a home electronics company which manufactures state of the art smart televisions. You want to develop a cool feature in the smart-TV that can recognise five different gestures performed by the user which will help users control the TV without using a remote. Let's have professor Raghavan introduce you to the problem statement:

### Understanding the Dataset
The training data consists of a few hundred videos categorised into one of the five classes. Each video (typically 2-3 seconds long) is divided into a sequence of 30 frames(images). These videos have been recorded by various people performing one of the five gestures in front of a webcam - similar to what the smart TV will use. 

The data is in a zip file. The zip file contains a 'train' and a 'val' folder with two CSV files for the two folders. These folders are in turn divided into subfolders where each subfolder represents a video of a particular gesture. Each subfolder, i.e. a video, contains 30 frames (or images). Note that all images in a particular video subfolder have the same dimensions but different videos may have different dimensions. Specifically, videos have two types of dimensions - either 360x360 or 120x160 (depending on the webcam used to record the videos). Hence, you will need to do some pre-processing to standardise the videos. 

 

Each row of the CSV file represents one video and contains three main pieces of information - the name of the subfolder containing the 30 images of the video, the name of the gesture and the numeric label (between 0-4) of the video.

 

Your task is to train a model on the 'train' folder which performs well on the 'val' folder as well (as usually done in ML projects). We have withheld the test folder for evaluation purposes - your final model's performance will be tested on the 'test' set.

 

To get started with the model building process, you first need to get the data on your storage. 

In order to get the data on the storage, perform the following steps in order

Open the terminal
 g0 down https://drive.google.com/uc?id=1ehyrYBQ5rbQQe6yL4XbLWe3FMvuVUGiL

 unzip Project_data.zip
 
 
### Two Architectures: 3D Convs and CNN-RNN Stack
 - After understanding and acquiring the dataset, the next step is to try out different architectures to solve this problem. 

 

 - For analysing videos using neural networks, two types of architectures are used commonly. One is the standard CNN + RNN architecture in which you pass the images of a video through a CNN which extracts a feature vector for each image, and then pass the sequence of these feature vectors through an RNN. This is something you are already familiar with (in theory).

 

- The other popular architecture used to process videos is a natural extension of CNNs - a 3D convolutional network. In this project, you will try both these architectures. Let's have professor Raghavan explain these two approaches.

Understanding Generators
Now that you understand the two types of architectures to experiment with, let's discuss how to set up the data ingestion pipeline. As you already know, in most deep learning projects you need to feed data to the model in batches. This is done using the concept of generators. 

 

Creating data generators is probably the most important part of building a training pipeline. Although libraries such as Keras provide builtin generator functionalities, they are often restricted in scope and you have to write your own generators from scratch. For example, in this problem, you need to feed batches of videos, not images. Similarly, in an entirely different problem such as 'music generation,' you may need to write generators which can create batches of audio files. 

 

In this segment, you will learn the basic concepts of a generator function and apply them to create a data generator from scratch.

 

Understanding Generators (External Links)
In this project, you will write your own batch data generator (explained in the next couple of lectures). Before moving to those lectures, we highly recommend that you develop an intuitive understanding of Python's generator functions. The following two resources explain the concept of generators well, we recommend that you go through both of them in this order:

Use Generators and yield in Python
Corey Schafer (YouTube video): Generator functions
You must have figured out from the above links that a generator object requires very less memory as compared to a function which is of primary importance in deep learning models.

 

Keras' Fit Generator
Now that you understand how generator functions work, let's see how Keras uses the 

fit.generator() method with a generator function (that you will write) to train the model.
