# Computer_Vision_Project


## Measuring Economic Development from Satellite Images using Deep Convolutional Neural Networks.

## Summary

For this project, I propose a new way of measuring economic development using large-scale satellite imagery data and state-of-the-art machine learning techniques based on deep convolutional neural networks. Traditional measures of economic development (e.g. GDP, literacy rate, infant mortality rate, etc.) are labor-intensive, expensive to obtain and unreliable (if even available) in developing countries. On the other hand, satellite imagery is freely available online and could be used to measure economic development by assessing land use. Specifically, analysis of land use through classification techniques using modern machine learning may serve as an inexpensive alternative way of measuring economic development particularly in the developing world. Here I describe the steps required, present some preliminary analysis, and highlight follow-up analysis.

## Methods

### Data Acquisition: (found in "Getting the data.ipynb") 
I constructed a new dataset for land use classification by combining class labels with satellite imagery. Specifically, locations (longitude/latitude) with land use class labels were acquired from the Urban Atlas, which is an open-source dataset of ~300 European cities covering 20 classes of land use. This dataset was used for establishing the ground-truth for training and testing purposes and extracting latitude/longitude coordinates of regions. Satellite images were obtained using the Google Maps Static API for the given sampling locations (latitude/longitude) as 224 × 224 images at a zoom level 17 (∼ 250m × 250m coverage per image). The final dataset consists of ∼ 20, 000 images distributed across 10 urban environment classes from 6 cities: Roma (Rome), Madrid, Berlin, Budapest, Barcelona, and Athens. This procedure was previously used by Albert et al. 2017. The dataset was split 80/20 for training and testing for classification purposes.

<img src="/images/classes_examples.png" width="85%">

### Classification Procedures: (found in "CNN validation and analysis.ipynb") 

I chose a recent technique from Deep Learning methods called Convolutional Neural Networks (CNNs) that has been extremely successful in classification of images. Convolutional Neural Networks are inspired by biological systems and operate by extracting features through many layers of connecting neurons. Given previous work, I decided to use the popular ResNet-50 architecture, which has achieved remarkable performance across a number of datasets including winning the 1st place on the ILSVRC 2015 classification task. It consists of an input layer, and a series of convolutional, RELU layers, and pooling layers, followed by an output layer. The CNN was implemented on Keras with TensorFlow backend. The network was trained using the dataset built, and splitting the data 80/20 for testing/training purposes, and the last layer of the network was used as feature extractor. 

<img src="/images/classes_examples_2.png" width="85%">

### Preliminary Results
Classification results showed relatively good accuracies (70-80%) in classifying satellite images into one of 10 classes. 

<img src="/images/classes_examples_3.png" width="85%">
<img src="/images/performance_plot.png" width="85%">


### Proposed Follow-up 
For future analysis, there are a number of things I’d like to try. First, in terms of improving performance, I’d like to create a larger and more balanced dataset with an approximately equal number of examples for each class (~10,000 images per class). This should improve performance and transferability. Second, I’d like to apply this technique to areas in the developing world where assessment of economic development is needed. Finally, future analysis should also include a comparison of this method to other more standard metrics for measuring development.

### Conclusion:
The analysis presented here combines modern machine learning techniques with freely available satellite data from Google Maps API to measure land use and provides a proof of concept for measuring economic development through an inexpensive yet robust method.

### Sources: 
Using convolutional networks and satellite imagery to identify patterns in urban environments at a large scale. A. Toni Albert, J. Kaur, M.C. Gonzalez, 2017. In Proceedings of the ACM SigKDD 2017 Conference, Halifax, Nova Scotia, Canada.

