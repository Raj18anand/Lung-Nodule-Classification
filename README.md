# Lung-Nodule-Classification
The basic aim of the project is to classify nodules and non-nodules from the given dataset. Two datasets have been provided for this purpose namely, the LNDb dataset and the LIDC-IDRI dataset. In order to classify nodules and non-nodules, we have used a **Convolutional Neural Network (CNN)** model.

### Dataset
We used the Lung Nodule Database (LNDb) and Lung Image Database Consortium (LIDC) dataset for this project. LNDb contains the CT Scans of around 294 patients and LIDC contains CT Scan images of around 358 patients.
The scans in LNDb dataset are in mhd format of dimension 512*512 and images of LIDC dataset are in tif file of dimension 64*64.

### Methodology

#### Data Preprocessing
In LNDb dataset, we have read mhd files and found the location of nodules with the help of masks provided in the dataset. Then we crop CT scans around nodule for nodule image of dimension 64*64 and we have given labels on the basis of data provided in csv by radiologists. While making classes of nodules and non-nodules, we encountered the problem of imbalanced data which means number of non-nodule data was very less compared to nodule data. Thus for balancing the data, we performed random crop on CT scans of non-nodule class. By doing this, ultimately, we got 423 images which contained 222 nonnodule images and 201 nodule images each of shape (64*64*1). After that we normalized pixel values of the data and split that into training set and testing set.
![lndb-dataset1](https://user-images.githubusercontent.com/55773147/178032439-a096b426-eb35-4728-b1fc-1b5279bcbd39.png)
![lndb-dataset2](https://user-images.githubusercontent.com/55773147/178032497-41545a29-52e0-4773-b557-f8a29f26bfbe.png)
For LIDC, we divide dataset into two folders namely nodule and non nodule folders which contains 170 and 188 images respectively. Once the dataset is uploaded we split dataset into training set, validation set and test set . After that we normalize training and validation data in the range of 0 to 1 using ImageDataGenerator class from keras preprocessing library . Thereafter, we read the dataset and set the target and batch size of (64,64) and 16 respectively.

### Model
We are using a Convolutional Neural Network (CNN) model. 
#### Training
For training the model we will take the dataset from train set and also we are validating the model using validation set. The training in performed for 10 epochs for LNDb dataset and 20 epochs for LIDC dataset. During training we monitor the loss. We use the loss function sparse_categorical_crossentropy. We have used SGD optimizer.
