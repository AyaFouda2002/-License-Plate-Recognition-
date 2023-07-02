# -License-Plate-Recognition-Using-Digital-Image-Processing

## Abstract
License Plate Recognition (LPR) is a digital image processing project that involves the automatic detection and recognition of license plates in images or video streams. The goal of this project is to develop a system that can accurately extract license plate information from images or video frames, which can then be used for various applications such as traffic management, parking enforcement, toll collection, and vehicle tracking.

## Introduction
Although the first automated system for recognizing car license plates (LPR) was introduced in the 1980s, numerous commercial systems emerged during the 1990s. Despite the abundance of LPR systems available on the market, research and development in this area persist, leading to the creation of new advanced methods for plate localization, character segmentation, and recognition.

Car license plates are now employed for various purposes, such as traffic control, border control, access control, parking time and payment calculation, searching for stolen cars or unpaid fees, and the need for accurate identification under different lighting conditions, the presence of random or structured noise in the plate, and nationality-specific features such as the plate's size and character order. To detect car plates more efficiently and eliminate human errors that may occur during manual procedures, we have developed an image processing algorithm that detects car plate characters with minimal error probability. Our implementation employs several techniques, including segmentation, adaptive thresholding, grayscale conversion, negative transformation, morphological operations, and contrast enhancement. By combining these image processing mechanisms, we have created a dependable tool for plate detection.

## Methodology

### Method 1: DataSet
The training and validation are done using a letters dataset that is used for ALPR (Automated License Plate Recognition) character training. The dataset is divided into training and validation sets. Each contains 36 classes: 10 numbers (0-9) and 26 letters (A-Z). The training set has 36 classes, each containing 24 images with a total of 864 images. As for the validation set, 36 classes, each containing 6 images, with a total of 216 images. The images in each class are of the same letter but with different shapes and slight changes to cover the biggest variables when it comes to tested models. The testing dataset “Car License Plates” was found on Kaggle with the source dataset uploaded on Make ML. It contains 433 car images with their plates from different angles and distances, both front and back plates, each labeled with bounding box annotations. The annotation is in Pascal VOC (visual Object Classes) format, used for object detection datasets.

### Method 2: Libraries
1-OpenCV
2-NumPy
3-Matplotlib
4-Pytesseract
5-PIL
6- Sklearn
7-TensorFlow
8-Keras

### Method 3: Processing
The idea is to use the libraries chosen to create a model that trains, validates and tests on the datasets used.
The training and validation are done on the letters dataset only to create a module that identifies the classes.
The main criteria the model is built on is the F1 score, which could be identified as the harmonic mean of
precision and recall:

                   F1 = 2 × (Precision × Recall) / Precision + Recall                 [1]

After training the model, the testing with the plates dataset is done through the following 
steps:
• The input image is read then converted using CV2 to grayscale.

• The contrast of the image is increased. Instead of directly using a contrast filter, morphological top/white hat (see eq. 2) and bottom/black hat (see eq. 3) operations are used. The functions can be explained as follows:

                                        Tw(f) = f − f ∘ b                              [2] 
                                        Tb  (f) = f • b − f                             [3]
where f is the original image and b is the structuring element used. Recall that ∘ represents the opening operation and the • the closing operations.

• A gaussian blur filter is then applied, then afterwards gaussian adaptive thresholding is done to convert the gray image to a binary one with desirable contrast.


### Results
1-converts the original color image to grayscale
<img src="xyyz.JPG" alt="Image" width="620px" height="auto">
2-Our image processing technique uses thresholding and contour detection to identify and highlight the car's edges and shapes. By displaying the thresholded image and the image with contours side by side
<img src="xyyz.JPG" alt="Image" width="620px" height="auto">
3-using Canny edge detection to highlight the car's edges and contours. By applying this technique, we can effectively extract the car's shape from the original image, resulting in a more striking and visually appealing representation.
<img src="xyyz.JPG" alt="Image" width="620px" height="auto">
4-using contour detection to create precise bounding boxes around the car's different parts, highlighting its shape and structure.
<img src="xyyz.JPG" alt="Image" width="620px" height="auto">
5-identifying and isolating the car's different parts using criteria based on size and aspect ratio
<img src="xyyz.JPG" alt="Image" width="620px" height="auto">
6-identifying and grouping  contours that are likely to be part of the same character. By comparing the size, shape, and position of each contour
<img src="xyyz.JPG" alt="Image" width="620px" height="auto">
7-Our image processing technique groups together similar contours and draws rectangles around them to better highlight the car's features. The resulting image shows the rectangles around the matched contours overlaid on the original image, resulting in a more detailed and visually interesting representation of the car
<img src="xyyz.JPG" alt="Image" width="620px" height="auto">
8-we segment the individual characters from the license plate image using a function called segment_characters
<img src="xyyz.JPG" alt="Image" width="620px" height="auto">
9-creating a subplot for each character in the char object and display the grayscale image of each character using the 'imshow' function
<img src="xyyz.JPG" alt="Image" width="620px" height="auto">

### conclusion
To sum up, using image processing techniques in various fields can be an effective method. For instance, it can be useful in car parking facilities to identify license plates and record entry and exit times, or in security systems to detect license plates and monitor any criminal activity. Moreover, the margin of error associated with this approach is relatively low, making it a reliable option for security and computational purposes that rely on the outcomes of the image processing technique utilized.











