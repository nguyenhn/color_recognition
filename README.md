# COLOR CLASSIFIER

This project focuses on color classifying by K-Nearest Neighbor classifier which is trained by R, G, B Color Histogram. It can classify White, Black, Red, Green, Blue, Orange, Yellow and Violet. If you want to classify more color or improve the accuracy you should work on the [training data](https://github.com/ahmetozlu/color_classifier/tree/master/src/training_dataset) or consider about other color features such as [Color Moments](https://en.wikipedia.org/wiki/Color_moments) or [Color Correlogram](http://www.cs.cornell.edu/rdz/Papers/ecdl2/spatial.htm).

## Quick Demo

<p align="center">
  <img src="https://user-images.githubusercontent.com/22610163/34917659-8497acae-f95a-11e7-93fb-f7cd6cc3128a.gif">
</p>

---
**What does this program do?**
1. **Feature Extraction:** Perform feature extraction for getting the R, G, B Color Histogram values of [training images](https://github.com/ahmetozlu/color_classifier/tree/master/src/training_dataset)
2. **Training K-Nearest Neighbor Classifier:** Train KNN classifier by R, G, B Color Histogram values
3. **Classifying by Trained KNN:** Read Web Cam frame by frame, perform feature extraction on each frame and then classify the mean color of it by trained KNN classifier.
---

## Theory

In this study, colors are classified by using K-Neares Neşghbor Machine Learning classifier algorithm. This classifier is trained by image R, G, B Color Histogram values. The general work flow is given at the below.

<p align="center">
  <img src="https://user-images.githubusercontent.com/22610163/34918580-b4c46b64-f965-11e7-8c6b-e7328813f7fa.png" {width=35px height=350px}>
</p>

You should know 2 main pheomena to understand basic Object Detection/Recognition Systems of Computer Vision and Machine Learning.

**1.) Feature Extraction**

How to represent the interesting points we found to compare them with other interesting points (features) in the image.

**2.) Classification**

An algorithm that implements classification, especially in a concrete implementation, is known as a classifier. The term "classifier" sometimes also refers to the mathematical function, implemented by a classification algorithm, that maps input data to a category.

For this project;

**1.) Feature Extraction** = Color Histogram

Color Histogram is a representation of the distribution of colors in an image. For digital images, a color histogram represents the number of pixels that have colors in each of a fixed list of color ranges, that span the image's color space, the set of all possible colors.

<p align="center">
  <img src="https://user-images.githubusercontent.com/22610163/34918867-44f5feaa-f96b-11e7-9994-1747846266c9.png">
</p>

**2.) Classification** = K-Nearest Neighbor Algorithm

K nearest neighbors is a simple algorithm that stores all available cases and classifies new cases based on a similarity measure (e.g., distance functions). KNN has been used in statistical estimation and pattern recognition already in the beginning of 1970’s as a non-parametric technique.

<p align="center">
  <img src="https://user-images.githubusercontent.com/22610163/34918895-c7b94d24-f96b-11e7-87da-8619d9bd4246.png">
</p>

## Implementation

[OpenCV](https://pypi.python.org/pypi/opencv-python) was used for color histogram calculations and knn classifier. [NumPy](https://stackoverflow.com/questions/29499815/how-to-install-numpy-on-windows-using-pip-install) was used for matrix/n-dimensional array calculations. The program was developed on Python at Linux environment.

In the “src” folder, there are 3 Python classes which are;

- **[color_classification_main.py](https://github.com/ahmetozlu/color_classifier/blob/master/src/color_classification_main.py):** main class

- **[feature_extraction.py](https://github.com/ahmetozlu/color_classifier/blob/master/src/color_histogram_feature_extraction.py):** feature extraction operation class

- **[knn_classifier.py](https://github.com/ahmetozlu/color_classifier/blob/master/src/knn_classifier.py):** knn classification class

**1.) Explanation of “feature_extraction_module.py”**

I can get the RGB color histogram of images by this Python class. For example, plot of RGB color histogram for one of the red images is given at the below.

<p align="center">
  <img src="https://user-images.githubusercontent.com/22610163/34919478-f198beb8-f975-11e7-8c1c-0a552f7cd673.jpg" {width=25px height=250px}>
</p>

I decided to use bin number of histogram which has the peak value of pixel count for R, G and B as feature so I can get the dominant R, G and B values to create feature vectors for training. For example, the dominant R, G and B values of the red image which is given at Figure 8 is [254, 0, 2].

I get the dominant R, G, B values by using Color Histogram for each training image then I labelled them because KNN classifier is a supervised learner and I deploy these feature vectors in the csv file. Thus, I create my training feature vector dataset. It can be found in the file which name’s is training_data.data under src folder.

**2.) Explanation of “knn_classifier.py”**

This class provides these main calculations;

1. Fetching training data
2. Fetching test image features
3. Calculating euclidean distance
4. Getting k nearest neighbors
5. Prediction of color
6. Returning the prediction is true or false

**“color_classification_main.py”** is the main class of my program, it provides;

1. Calling [feature_extraction.py](https://github.com/ahmetozlu/color_classifier/blob/master/src/color_histogram_feature_extraction.py) to create training data by feature extraction
2. Calling [knn_classifier.py](https://github.com/ahmetozlu/color_classifier/blob/master/src/knn_classifier.py) for classification

You can find training data in [here](https://github.com/ahmetozlu/color_classifier/tree/master/src/training_dataset).

You can find features are got from training data in [here](https://raw.githubusercontent.com/ahmetozlu/color_classifier/master/src/training.data).

## Conclusion

I think, the training data has a huge important in classification accuracy. I created my training data carefully but maybe the accuracy can be high with more suitable training data.

Another important thing is lightning and shadows. In my test images, the images which were taken under bad lighting conditions and with shadows are classified wrong (false positives), maybe some filtering algorithm should/can be implemented before the test images send to KNN classifier Thus, accuracy can be improved.

## Citation
If you use this code for your publications, please cite it as:

    @ONLINE{vdtc,
        author = "Ahmet Özlü",
        title  = "Color Classifier",
        year   = "2018",
        url    = "https://github.com/ahmetozlu/color_classifier"
    }

## Author
Ahmet Özlü

## License
This system is available under the MIT license. See the LICENSE file for more info.
