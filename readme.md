1. DL Formulation
This is an Object detection problem, create a dataset by capturing the road images, annotate the images by drawing a bounding box around them. Train an Object detection model using pothole images and bounding boxes such that given an input image, classify/identify as a pothole or not and if it contains a pothole localize it by drawing a bounding box around it in realtime.

2. Performance Metrics
IoU (Intersection over Union):
In object detection we localize the detections by drawing bounding boxes around the objects, so we train a model to output a box that fits perfectly around an object. IoU (Intersection over Union) is used to measure our prediction is correct or not by calculating how much the predicted bounding box overlaps with the ground truth bounding box


image credit: jonathan-hui
In the above image blue box is the ground truth box and orange box is the model prediction, IoU is calucated by dividing area of overlap (dark blue region) by area of union (light blue + dark blue). IoU values ranges from 0 to 1. If IoU is greater than a threshold (generally 0.5 is set as threshold) then the prediction is considered as True Positive (TP) else False Positive (FP).

mAP (mean Average Precision):
Standard metrics accuray, precision, recall etc. cannot be used as an image might contain multiple objects of different classes, therefore mAP is used as the performance metric for object detection. IoU helps us to determine whether a prediction is True Positive (TP) or False Positive (FP), using these values precision and recall is calculated. Average Precision (AP) for each class is calculated as the area under the Precision Recall curve. mAP score is calculated by taking the mean of Average Precision over all classes. 
