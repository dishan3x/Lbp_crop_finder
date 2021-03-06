# Object detection using local binary classification 

Developer : Dishan Nahitiya</br>
Area      : Image analysis


## Objective

Develop an image classifier to identify the nearest class label of canopies based on their texture intensitivity. 

##  Methodology

 There are number of image classification algorithm in the field of image analysis. I will make this project as an opportunity to explore about local binary pattern search , an efficient texture analysis method which is widely used in the areas of
 - facial recognition 
 - face detection
 - verication purposed of the facial images
 
 This goal of this project is to try to make a classifier which identify the different textures of crop types and soil types.  

## What is local binary pattern search ?

Local binary search is a texture based classification algorithm which generates a pattern sequence. This basic technique uses a 3 * 3 binary grid which traverse through all pixel , use and calculate
threshholding arround the center pixel and generate a 8 bit number.LBP operator is then applied on the image to extract local features represented by histogram.


<p align="center">
  <img src="images/readme/histpogram_transoformation_1.PNG"  alt="" height="200" width="500"/>
  <p align="center">Figure 1. lbp transformation</p>
</p>

</br>
</br>

<p align="center">
  <img src="images/readme/histogramEquation.PNG" alt="" width="500"/>
  <p align="center">Figure 2. Histogram equation</p>
</p>

<p align="center">
 <img src="images/readme/validation.PNG" alt="" height="80" width="220" />
  <p align="center">Figure 3. Binary Validation .</p>
</p>

Inorder to identify the similarities between histograms generated by image, the 
model needs to get support of a distant classifier. This project uses  Kullback Leibler divergence 
which has the ability to identify the probability distributions in histograms.
<br>
<p align="center">
 <img src="images/readme/Kullback.PNG" class="center" alt="" height="75" width="320"/>
  <p align="center">Figure 4. Kullback Leibler divergence identification .</p>
</p>


 This algorithm provides the information lost in the mapping process  and  greater the loss resembels dissimilarity between the distributions.


## Challanges
 1. When analysing images , due to various image propertise for instance noise, brightness, shape differences, orientation difference and etc, the models might not be able to identify divergense in histograms. As a solutiuon I tried multiplying input images count using data augmentation algorithms. 
 This would give the ability to create different senario of each image and identify the texture similarities in each images.
 2. Local binary pattern operates in 2 x 2 dimentions forcing to change the image to gray scale pattern. Unfortunetly this process
  hinders to gather accurate information about images. This may affect in choosing the right cluster class in each image.  

## Sketch 
<p align="center">
  <img src="images/readme/lbp_process.png" class="center" alt="" height="150" width="500"/>
   <p align="center">Figure 5. Project flow.</p>
</p>


  
## Results and Discussion 

 - The labels, I aquired for this project are contaminated due to having 2 or more classes in the same image. Therefore the modler will falsely identify the wrong classes. 
 - Since  Kullback Leibler divergence is not a highend distant classifier it has the ability to produce false output.
   inorder get a proper classification it better use a classifier such as support vector machines, k-means and etc. 
   Moreover in modern day deep nural networks has the ability to identify object much accurately.
  - Algorithm in local binary search depends on the grid size used to traverse along the pixels in the image. The radius would determine the accuracy
  each texture. According to output, it visible that increase of radius will increase divergense and the execution time in each simulation. 
 
## Conclusion 

 - Hard to identify the intensities due to unorthodox shapes of each plants and number of leaf count in an image. 
 - The best way is to gather more label images and test data in them.  
 - It was easy to identify flat areas in an image. The edges can identify regardless the size of object.
 - When there is a increase of radius, divergense value and the execution time is propotional to the radius.  
 
## Future work
 - Adopt otsu method to isolate dense areas to clear the noise in images.  
 - I already started working with svm and cnn networks. Need some fine tuning in those project which I believe that I could get more accurate results in classifying crop medels. 
## References

1.[Vupputuri, A. and Meher, S., 2015, April. Facial expression recognition using local binary patterns and kullback leibler divergence. In 2015 International Conference on Communications and Signal Processing (ICCSP) (pp. 0349-0353). IEEE.](https://ieeexplore.ieee.org/document/7322904)

2.[Scikit-image.org. 2020. Local Binary Pattern For Texture Classification — Skimage V0.17.Dev0 Docs. [online] Available at: <https://scikit-image.org/docs/dev/auto_examples/features_detection/plot_local_binary_pattern.html>.](https://scikit-image.org/docs/dev/auto_examples/features_detection/plot_local_binary_pattern.html)

3.[kaggle.com. (n.d.). Image manipulation / augmentation with skimage. [online] Available at: https://www.kaggle.com/tomahim/image-manipulation-augmentation-with-skimage](https://www.kaggle.com/tomahim/image-manipulation-augmentation-with-skimage)