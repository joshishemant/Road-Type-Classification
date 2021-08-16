# Road-Type-Classification
To classify a road based on its type i.e., tarcoal, paver, cement or kaccha(mud) road.

> Dataset 
- The dataset was prepared manually by capturing or collecting photos of different types of roads. The types being : Tarcoal road, Paver blocks, Kaccha(mud) road and Cement road. - The dataset contains 100 images per class, the total being 400. 
- It was seen that the images are taken in different lightning conditions to increase the variation in available data.
![image](https://user-images.githubusercontent.com/67290562/129612344-63b60549-2a26-42cf-838b-021e30ee8217.png)

> Preprocessing 
- The preprocessing consists of reshaping all the images to one dimension to incorporate uniformity in the available data.
- Every image was converted to grayscale to reduce complexity in processing.

> Feature Extraction 
- Keypoint detection and feature extraction was carried out on every image.
- Here, ORB was used to detect and extract the feature from images.
- ORB is a fusion of FAST keypoint detector and BRIEF descriptor with some added features to improve the performance. It is robust, rotation invariant and resistant to noise. Moreover it's faster when compared to SIFT or SURF and is not patented.
- The maximum size of the feature vector by ORB is 500 x 32.
![image](https://user-images.githubusercontent.com/67290562/129612386-fa2def8d-1ee1-40b5-978b-e946346c8cfc.png)

> Dimensionality Reduction 
- The dataset has 400 photos in total, so the total approximate feature given by ORB on the whole dataset would sum up to 2 lakh x 32. For the given dataset it was ~1.4lakh x 32. - So to train the data into classifier dimensionality reduction was carried out on the available feature vector. This was done using KMeans Clustering.
- The value of k in KMeans was calculated by the WCSS (within cluster sum of squares) method also known as the elbow method. Here, the value obtained was 8. d. The feature of each image was divided into 8 clusters by non-supervised learning. e. So, the final shape of the feature vector data was reduced to 400 x 8.
![image](https://user-images.githubusercontent.com/67290562/129612410-de22a01c-d259-43d2-b307-28d50f442e55.png)

> Training Classifier 
- The features obtained after applying KMeans on the previously obtained ORB features were then labeled according to the class they belong to.
- These labeled features were then split into test and train data in the ratio of 3:7 and transformed using standard scaling.
- Finally the train data was given as input to the Random Forest Classifier.
- The test data was then validated and the confusion matrix was predicted with the accuracy value.
![image](https://user-images.githubusercontent.com/67290562/129612451-f7f8917e-89d9-4d95-b18a-eca57f09569d.png)

> Prediction The classifier was given a random image feature vector to classify it into one of the classes or predict the road type.

![image](https://user-images.githubusercontent.com/67290562/129612307-deb0b178-8e58-4ad5-8936-b632525a33e7.png)
