# Cats and Dogs Classifier
## Project description
A binary classification problem for classifying cats and dogs. The project covers the following concepts:

1. Checking data for imbalance and if necessary use augmentation using keras ImageDataGenerator
2. Since dataset was a subset of data from kaggle for the original project, i downloaded further data from kaggle to balance the classes
3. Script in kaggle_data_splitter creates train, validation, test split for the project and organizes the folders automatically
4. To save memory the model uses .flow_from_directory method as .flow loads data to the memory. The data is loaded in batches to the GPU using a generator function.
5. The GPU memory allocation is further controlled using tensorflow .set_memory_growth method
6. The images are resized to 224\*224 as the original images are of higher dimensions and a 1080ti was available, hence with enough VRAM
7. The images are normalized using parameters rescale and further the channel axis is dropped, thus converting the images to grayscale. The batch size is set to 32 and shuffle is turned off for the test set, for consistency in results
8. A keras sequential model is used for simplicity with 4 Convolutional layers and 3 Dense layers. The kernel size are kept at 5 and a stride of 2 for maxpooling layer as to decrease the learned parameters. Dropout is used for regularization
9. Standard Adam optimizer with categorical cross entropy as loss functions
10. The model uses callbacks for saving checkpoints and stats for tensorboad
11. A confusion matrix with classification report is generated which are saved to a .PNG and CSV files
12. The final model is saved

## Flask Application
1. A flask application is available which uses the trained model to predict on uploaded images
2. Image uploaded is passed to a preprocessing function which resizes and reshapes the image as per required by the input layer of the model
3. Then the image is passed to a prediction function which generated output as a one hot encoded list
4. Using conditional statements outout is generated as a string 'cat' or 'dog'

## Installation Requirements
I highly recommend using anaconda virtual environment for this, or any python project, since anaconda automatically configures the correct(conflict free) version numbers for python libraries. check the required imports in environment.yml file.

## how to run
follow the steps to run the project:

1. Install anaconda (https://docs.anaconda.com/anaconda/install/)
2. open anaconda terminal if you are using Windows (for MacOS & other Linux based distros use the terminal)
3. Install git by running the following command from the anaconda terminal 'conda install -c anaconda git'
4. clone this repository by entering 'git clone https://github.com/hamzamk/Sample_ClassData_generator/'
5. cd into the cloned directory(if you haven't)
6. run the following command 'conda env create -f environment.yml' (https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)
7. activate the 'cats_vs_dogs' environment by running the following command 'conda activate 'cats_vs_dogs'
8. run jupyter notebook by entering the following commdand 'jupyter notebook'
9. locate the .ipynb file in the new browser tab which opened automatically and run the notebook
