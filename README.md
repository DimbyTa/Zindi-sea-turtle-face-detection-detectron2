# Kaggle Notebook for Zindi competition:  Local Ocean Conservation Sea Turtle Face Detection

The notebook in this repository contains code for training and evaluating an object detection model using Detectron2 (https://github.com/facebookresearch/detectron2). We extend the basic training process of Detectron2 to include early stopping mechanism. The model is trained on the turtle dataset for the Local Ocean Coservation Sea Turtle Face Detection (https://zindi.africa/competitions/local-ocean-conservation-sea-turtle-face-detection) which asks participants to train a model for the bounding box on turtle face in every images.

## Environment

Kaggle notebook with two T4 GPUs

## How to run it

 1. Make sure you uploaded the compressed dataset into Kaggle.
 2. Inside the notebook, there is a line specifying to unzip the compressed dataset into the environment. Choose between the 512 or the 1024 pixels set of images.
 3. change the variable image_folder accordingly to the set of images you use.
 
## Early stopping mechanism

To include early stopping mechanism, we need to extend HookBase and build a custom DefaultTrainer. 
HookBase is in charge of the training process in Detectron2, while DefaultTrainer is a class in charge of managing the training process. 
In order to add early stopping, we need to override the method after_step() of HookBase. after_step() is in charge of what the trainer should do after each step of the training, mainly here, evaluate the model and its performance, see if it improved, if not, see if the patience was exceeded, and if it is the case, stop the training. More on that inside the notebook.

## Metric

In order to asses the performance of the model on bounding boxes generation, the Intersection over Union metric (IoU) was used.

## Public leaderboard score

Achieved a score of 0.9135 on public leaderboard, profile: Taratra_N0_on3
