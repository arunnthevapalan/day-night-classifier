# Day Night Images Classfier
This repo contains the implementation of a classification of day-night images by Image Processing using OpenCV and zero Machine Learning.

## Pre-requisites

The project was developed using python 3.6.7 with the following packages. GPU is not required.

- numpy==1.16.4
- pandas==0.24.2
- seaborn==0.9.0
- matplotlib==3.0.3
- opencv-python
- jupyterlab

Installation with pip:

```bash
pip install -r requirements.txt
```

## Dataset

The day/night image dataset consists of 200 RGB color images in two categories: day and night. There are equal numbers of each example: 100 day images and 100 night images. This would give us a balanced dataset.

*Note: All images come from the [AMOS dataset](http://cs.uky.edu/~jacobs/datasets/amos/) (Archive of Many Outdoor Scenes).*

## Approach

Step 1: Load the datasets and visualize
- Visualizng the dataset gives us an understanding of the data. We try to find some  distinguishing features: day images are  much brighter, generally, than night images. Night images also have these really bright small spots, so the brightness over the whole image varies a lot more than the day images. There is a lot more of a gray/blue color palette in the day images.
  
Step 2: Preprocess the data
- All the input data should be in a consistent form. We resize all the images to a fixed size and encode the target variables. Multiple approaches like One-Hot, Label encoding can be used for this.

Step 3: Feature Extraction
- The average brightness using HSV colorspace. Specifically, we'll use the V channel (a measure of brightness), add up the pixel values in the V channel, then divide that sum by the area of the image to get the average Value of the image.

Step 4: Build the classifier
- A simple classifier that sets a threshold value of average brighness to separate between the two classes.

Step 5: Evaluate the model and optimize
- Here the model is tested for metrics such as accuarcy and the optimal threshold value is chosen.

## Conclusion

Often when it comes to AI problems, we try to use our Machine Learning algorithms, or Deep Learning concpets to gain the best accuracy. However these methods are data hungry and requires high computational power, and works well only when there are sufficient such resources. Here we try to classify the images as if it was taken in day or night using traditional basic Image Processing technique and got an accuracy of **93.75%**.
