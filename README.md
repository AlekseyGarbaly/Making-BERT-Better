# Making-BERT-Better

The BERT model on Google Colab already has instructions, this ReadME is just outlining what parts were changed and used

User Manual for BERT using Google Colab
	The Google Colab notebook already has text and instruction, but a few important steps will be shown here. The original notebook is shown in [3] so only the parts that are changed or are important will be displayed as steps as once certain things are entered, most of the remaining steps can be automatically run.

**Environment Setup**
BERT was originally trained under TensorFlow 1.11.0, it still works under many versions but 1.15 was chosen as that was the moist recent TensorFlow version in anaconda before TensorFlow 2.0.0. With the newer TF v2 version, many aspects of BERT have to be changed as some methods were removed and changed, look the TensorFlow 2 documentation for more information.
[] pip install tensorflow==1.15

The notebook has a cell that allows you to connect to a bucket that is found in Google’s cloud service, this will output all model checkpoints and evaluation directly to the chosen bucket. The OUTPUT_DIR is the name of the folder that will be created to contain all the outputs, and the BUCKET: option lets you pick what bucket you would like to use. The first time the cell is run a short verification is performed to make sure that the right person is trying to access the given bucket.

![GitHub Logo](C:/Users/user/Pictures/BERT1.png)
Format: ![Alt Text](url)

**Data input**
This cell lets you import and locally upload your data into the Google Colab notebook. Once its been uploaded then it can be accessed locally. You can also just find and drag files in the appropriate places, but this built cell does the work for you. The first time the cell is run a short verification is performed to make sure that the right person is trying to access the appropriate drive.

**Sequence Length**
The sequence length can be changed, the default was 128 but it was changed to 64 after preprocessing the twitter data. Generally, the longer the sequence length, the more computationally expensive the model will be to train.

**Creating the Model**
The FC architecture of the model can be changed in this cell, but the guidelines to do so can be found in BERT’s original source files.

The major hyper-parameters can be changed in this cell. There is a limit on the batch size as you get a limited amount of memory allotted in Google Colab so if this number is set too high the model will terminate training and notify you. The learning rate and epoch number shown were used as the reference numbers. Warm-up describes how fast the learning rate will start up, it makes the learning rate small at first and the increases it over a few iterations or epochs until it reaches the actual learning rate.

**Model Evaluation**
After the model has been trained and evaluated, a metrics csv file is generated containing a list of the hyper parameters and many of the metrics found in the model. There are two places that the file can be put, your local cloud drive or on your bucket on the folder that was specified at the beginning. The cell below gives the user the ability to save the file their chosen drive directory with using their chosen file name.
 
The cells used to save the file on the bucket is shown below. The gsutil command lets you access your cloud storage and copies the csv file from your drive to your bucket. Your particular Project ID should be entered in the “project_id” line, ad your bucket name has to be entered in the bucket_name line.
 

