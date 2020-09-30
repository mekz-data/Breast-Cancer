# Breast Cancer
Creating a Convolutional Neural Network with Keras to detect cancer in breast histopathology images.
 
This was my first ever deep learning project. Although the model was not incredibly complex, I learned a lot and gained
quite a bit of appreciation for the advances in artificial intelligence wherein a novice like myself can build a model that can 
accurately detect cancer in images. It gave me goosebumps about the implications of the future of AI and how well it can be used to 
benefit society. 

## Project Overview
- The cancer we're detecting in the images is known as Invasive Ductal Carcinoma (IDC). Makes up ~80% of all breast cancer cases. 
- Data consisted of 162 slide images (patients) that were cut into 277,524 patches of 50x50 pixels.
- The images are originally from a 2014 study which you can see [here.](https://engineering.case.edu/centers/ccipd/sites/ccipd.case.edu/files/Automatic_detection_of_invasive_ductal_carcinoma_in_whole.pdf)
- Images were preprocessed and augmented with Keras's built in ImageDataGenerator. 
- Keras was also used to create the CNN model. 
- The model ended up yielding an accuracy/F1 score of 87%.
 
## File List
**Final Report.pdf:** Written report of the project that condenses much of the information from the jupyter notebooks contains many of
the visualizations. Additional insights and analysis are in there as well. 

**2014 Study.pdf:** A copy of the initial study that this project is based on. **Note:** I did not contribute to this study. It's merely creating a frame of reference. 

<ins>**Jupyter Notebooks:**</ins><br>
**0 - [Image Sorting:](https://github.com/Huntsworth7/Breast-Cancer/blob/master/0%20-%20Image%20Sorting.ipynb)** Using scripting to re-sort the images so as to utilize the Keras built in DataImageGenerator.

**1 - [EDA:](https://github.com/Huntsworth7/Breast-Cancer/blob/master/1%20-%20EDA.ipynb)** Exploratory data analysis of the images.

**2 - [Preprocessing and Modeling:](https://github.com/Huntsworth7/Breast-Cancer/blob/master/2%20-%20Preprocessing%20and%20Modeling.ipynb)** Preprocessing the images to load them into our model. Building and evaluating the model along with thoughts on the best threshold to determine our target variable. Final thoughts.

## Code and Resources used:
- **Python Version:** 3.7
- **Packages:** [split-folders](https://pypi.org/project/split-folders/), pandas, numpy, matplotlib, scikit-image, seaborn, tensorflow, keras, scikit-learn 
- **Article:** [How to Load Large Datasets From Directories for Deep Learning in Keras](https://machinelearningmastery.com/how-to-load-large-datasets-from-directories-for-deep-learning-with-keras/)
- **Article:** [Tutorial on using Keras flow_from_directory and generators](https://medium.com/@vijayabhaskar96/tutorial-image-classification-with-keras-flow-from-directory-and-generators-95f75ebe5720)
 
## [Features:](https://github.com/Huntsworth7/Breast-Cancer/blob/master/1%20-%20EDA.ipynb)
As the dataset was images, features had to be created from scratch. Thankfully, the images were well labeled and a dataframe was created that consisted of:
- **patient_id** - the unique patient id number that the image came from. 
- **x** - the x coordinate of the image
- **y** - the y coordinate of the image 
- **target** - our target variable: did the image contain cancer?
- **image** - filename of our image.  

## [Image Sorting:](https://github.com/Huntsworth7/Breast-Cancer/blob/master/0%20-%20Image%20Sorting.ipynb)
- Dataset was originally organized by patient_id and target variable. 
- Python scripts were run to consolidate the images so that the split-folders package could be used. 
- Split-folders was used to split the images into a .7, .15, .15 ratio for training, testing, and validation sets respectively. 

## [EDA:](https://github.com/Huntsworth7/Breast-Cancer/blob/master/1%20-%20EDA.ipynb) 
EDA was performed but did not yield a lot of insights. Notables included:
- Imbalanced dataset with 28% of the images containing cancer. 
- Cancerous images appeared to be a lot more purple than non-cancerous. 
- 61 out of 279 patients had imagesets in which a majority of the images have cancer contained in them.
- On the other hand, 43 of our patients have less than 10% of their images containing cancer within them.

## [Model Building:](https://github.com/Huntsworth7/Breast-Cancer/blob/master/2%20-%20Preprocessing%20and%20Modeling.ipynb)
- A Sequential CNN model was built containing layers of convolution, max pooling, dropout, flatten, and ending with multiple dense layers.   
- Images were preprocessed with ImageDataGenerator and a variety of augmentations were added.
- Images were shuffled into our model in batch sizes of 130. 
- Model was fit over 35 epochs. 

## [Model Performance:](https://github.com/Huntsworth7/Breast-Cancer/blob/master/2%20-%20Preprocessing%20and%20Modeling.ipynb)
- Model achieved 88% accuracy and f1 score. 
- Different thresholds were experimented with to see how they affected performance and diagnoses for patients. 
- .4 thresholds seemed to yield the best results in terms of minimizing false negatives (predicting no cancer where cancer is present) without creating too many false positives (predicting cancer where there is none). 
 
## Final Thoughts:
-**Not all classification problems are created equally.** F1 score and Accuracy aren't not necessarily the most important metrics depending on what is being prioritized in a given problem. This is especially
the case when the ramifications of a false negative can be so detrimental to a person's life. 
 
