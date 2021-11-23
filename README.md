# Object Detection Persian Digit Detection
In this Persian project, I identify the Persian Digits in a given image. An example of the results of my project is below:  
![image](https://user-images.githubusercontent.com/67642255/142971398-6dd777eb-524d-4f95-bd20-e5c0d3cfbf54.png)  


This repository consists of three parts.   

**1-** A draft of the first, successful effort: You can ignore the draft, it was my first successful classifier. unfortunately, it wasn't saved in my personal space. Therefore, I missed it.   
**2-** A classifier: classifier is a model that recognizes between the Persian digits and non-Persian digits. in the final part of this notebook, you can see a function that performs all the tasks automatically.     
**3-** A function: I separated the function that can recognize between Persian digits objects in images and other objects. this function needs two paths, one belongs to the image and the other belongs to the classifier model.

# Data:
In the first part, I made a dataset from the following data:
- Images of Persian digits, I made this dataset by using 160 Persian fonts and plt library. They were 300 dpi. I shrank them to about 68 dpi by removing the empty part of the images and then resizing it to 32by32. 
- Persian handwritten digits. link: https://raw.githubusercontent.com/sraeisi/MachineLearning_Physics/master/Data/Farsi_digits_X.npz
- Image of non-digits. link: https://github.com/iilabau/AUTNTdataset/archive/refs/heads/master.zip
- Image of non-digits. link: https://github.com/Vishwesh4/Text-vs-Non-Text-Classifier
- Images of Persian non-digit text: http://ebrahimpourlab.ir/download-dataset-sruphn/
- Images of Persian non-digit text: https://www.kaggle.com/amir137825/persianocrdataset/version/1?select=Shotor_Words.csv   

I copy all non-digit images to the same directory, and then I read them and after a preprocessing, I convert them to np-array.  
Then, I concatenate the np-array of Persian digits and non-digit np-array. 

# Model

I made a binary CNN classifier. Then I trained it with my data for different epochs. 
I tested different bach-sizes: 32, 64, 128.
The accuracy of the model on test data was .997. 
Here you can see the confusion matrix:   
![image](https://user-images.githubusercontent.com/67642255/142972658-88dc7405-ccca-44fe-adc7-0a2bd8b31d0c.png)  

The plot of the accuracy of train data and validation data is bellow:   
![image](https://user-images.githubusercontent.com/67642255/142972737-c5604dd3-949d-480f-81eb-ff64e5f5c210.png)   
Then, I saved the model and downloaded it. 


# Persian Digit Recognizer Function:

I made a function to implement the model on the given image. 
- Firstly, this function receives the path of image and the path of classifier model I introduced it in the previous part. 
- Then, it read the image.
- Afterward, I put a part in the function to preprocess images and detect objects in images. 
- I crop images from these objects. 
- I save the position of these objects for later use.
- I load the classifier using the given path. 
- I give the cropped images of objects to the classifier after resizing them to the appropriate size of classier input.
- I save the prediction of the classifier for the label of these objects. 
- I separate those objects labeled as Persian digits. 
- I add rectangle lines to the original image for those objects labeled as Persian digits on their position in the original image. 
- As an output, I show two images, on the left the images with objects labeled as Persian digits, and on the right the image with all recognized objects. 


You can see an example of implementation of image:   
![image](https://user-images.githubusercontent.com/67642255/142973714-f8707751-aa1c-4cf6-9e80-05d4a8f81036.png)   



