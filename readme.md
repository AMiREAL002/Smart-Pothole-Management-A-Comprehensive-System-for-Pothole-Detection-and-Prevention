**1. DL Formulation**
This is an Object detection problem, create a dataset by capturing the road images, annotate the images by drawing a bounding box around them. Train an Object detection model using pothole images and bounding boxes such that given an input image, classify/identify as a pothole or not and if it contains a pothole localize it by drawing a bounding box around it in realtime.

**2. Performance Metrics**
IoU (Intersection over Union):
In object detection we localize the detections by drawing bounding boxes around the objects, so we train a model to output a box that fits perfectly around an object. IoU (Intersection over Union) is used to measure our prediction is correct or not by calculating how much the predicted bounding box overlaps with the ground truth bounding box

 IoU values ranges from 0 to 1. If IoU is greater than a threshold (generally 0.5 is set as threshold) then the prediction is considered as True Positive (TP) else False Positive (FP).

mAP (mean Average Precision):
Standard metrics accuray, precision, recall etc. cannot be used as an image might contain multiple objects of different classes, therefore mAP is used as the performance metric for object detection. IoU helps us to determine whether a prediction is True Positive (TP) or False Positive (FP), using these values precision and recall is calculated. Average Precision (AP) for each class is calculated as the area under the Precision Recall curve. mAP score is calculated by taking the mean of Average Precision over all classes. 

**3. Modeling:
i. SSD MobileNet:**

SSD (Single Shot MultiBox Detector) object detection consists of 2 main stages namely feature extraction and detection. In feature extraction stage input image of shape 300x300x3 (height x width x channel) is passed through a CNN without classification layers to extract useful features.
![1_0f2RhDHrZW2KNNp_bLnF-w](https://github.com/AMiREAL002/Smart-Pothole-Management-A-Comprehensive-System-for-Pothole-Detection-and-Prevention/assets/84368610/6692b731-b1f8-4563-9c23-98c288c1f8fa)
As we can see in the above picture, in the orginal paper VGG-16 is used to get features of shape 38x38x512. To detect object at different scales these features are passed through various convolution layers to get 6 feature maps of different size and number of channels.

In detection stage bounding boxes and class scores are generated using convolution . SSD makes 8732 predictions (default/anchor boxes) using 6 layers, for each default box, class confidence score for each class and 4 offsets relative to the default/anchor boxes shape are calculated. Only those default boxes which have high overlap (IoU) with gound truth boxes are considered and remaining boxes are ignored. Bounding boxes are adjusted using offset values and output a class label as the class with high confidence score. As a post-processing Non-Maximum Suppression technique is applied to avoid multiple boxes for a single object.

MobileNet is a light weight and efficient Convolution Neural Network developed mainly for mobile vision applications. MobileNet uses depthwise separable convolutions. It significantly reduces the number of parameters therefore requires less storage/memory resources and less computational resources also reduced computation time.

In standard convolution application the application of filters across all input channels and the combination of these values are done in a single step. Depthwise seperable convolution on the otherhand breaks this down into two parts the first is depthwise convolution in which convolutions are applied on each input channel seperately and then pointwise convolution which perform the combining stage.

**The Below video shows the output of the model:**


https://github.com/AMiREAL002/Smart-Pothole-Management-A-Comprehensive-System-for-Pothole-Detection-and-Prevention/assets/84368610/9be1a9a9-5fcd-4f98-8ba8-cb3b6ab740b5

