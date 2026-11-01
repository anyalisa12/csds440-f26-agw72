Research Diary Template
---------------------------
Answer all questions. For those which do not apply write "Not Applicable." Place
the completed diary and all other resources indicated below in a folder "Week_n" in
your cwru-courses repository, where n is 1 to 5. I expect the diary to show clearly
that you have spent at least 6 hours on this work (including the time spent
preparing this diary).
1. Briefly summarize your knowledge of the area you are researching as of last
week, and your plans for the current week from Q7 of your last diary. If this is
the first diary write "Not Applicable."

Answer: This week I explored a type of black box predictions; federated learning. Federated learning involved the study of a ML model which takes inputs from multiple training sets, develops a global average and distributes that average to the clients for testing. And the paper I read was related to my field of smart manufacturing and AGVs. Because in this class, I have been learning lots of new content I decided my project should use data and concepts being applied in my field of mechanical engineering. 

2. List all resources you have read or looked at this week, along with the time you
spent on each one (to the nearest 1/2 hour is enough). For web pages, blog posts,
videos etc, provide links and titles. For papers, provide links and citations. For
code written, provide a Jupyter notebook in the Week_n folder and list the file
name (as a link) here. For AI tools, provide a transcript of your session in a
separate file in the Week_n folder, and list the file name (as a link) here. The
transcript file can be a text file or pdf. Do *not* link to chat sessions directly.

Answer: Federated Learning for improved prediction of failures in AGVs. It took me more than 6 hours understanding the contents of this paper because I havd to use chatGPT to understand AGVs then Federated learning and relate how they used CNNS. I spent about 2 hours understanding the analysis and discussing with my PI what data and ML approaches like this can mean to writing my thesis and using ML for a few predictions in my smart manufacturing predictions.

3. Summarize what you have learned **this week** from the resources above. Be
clear, detailed and precise. It is ok to be uncertain about the content. Do **not**
copy/paste content from any resource.
Answer: From my paper "Federated Learning for improved prediction of failures in AGVs", I saw how machine learning models can compare other distributed knowledge and make predictions in a black box scenario. 
Focus on continuous production optimization because AGVs work/primarily operate in transportation in factories
I took time to understand the real-time analysis of the AGV data and how ML can enrich local and remote monitoring of the AGVs health and improve consistency of production
The experience gained by each AGV is precious, and appropriate predictive maintenance tools may detect the first signs of failure in industrial environments

5. If you implemented/ran any code or algorithms from the resources or while
investigating any new ideas, describe what you did. Link to a jupyter notebook in
your Week_n folder showing the runs. You may also include python files containing
code in your Week_n folder. If so, their content should be described here. If you
forked another repo or imported pre-built code, please provide a link. If an AI
tool wrote part of the code, please provide a session transcript in the Week_n
folder and link to it here. If any part of the code did not run or did not behave
as expected, describe your best guess why and possible fixes.
Answer: Yes, I debugged my code and wrote a new CNN model to make a federated learning prediction because I might use this specific type of black box preddictions.
I used CWRU bearing data and cited the work discovered in Jianjig's paper 2 weeks ago;

import numpy as np
import random
import requests

from scipy.io import loadmat
from io import BytesIO

from sklearn.model_selection import train_test_split
from sklearn.metrics import confusion_matrix
from sklearn.metrics import classification_report

import tensorflow as tf

from tensorflow.keras.models import Sequential

from tensorflow.keras.layers import (
    Conv1D,
    MaxPooling1D,
    Dense,
    Flatten,
    BatchNormalization,
    Dropout

WINDOW_SIZE = 800
STEP_SIZE = 800
NUM_CLIENTS = 50
ROUNDS = 20

LOCAL_EPOCHS = 1
BATCH_SIZE = 16
LEARNING_RATE = 0.01 

label_map = {

    "normal": 0,
    "ball": 1,
    "inner_race": 2,
    "outer_race": 3

7. Summarize any specific points of confusion, uncertainty or difficulty from your
reading or implementation that arose from your readings or implementations this
week. This can partly overlap with your answer (3).
Answer: I am still learning how to use batch normalization and the concept of it. This has been covered in class in the Monday lecture and I will read the textbook once more to understand deeper

9. List specific goals you would like to accomplish for next week and action items
aligned with these goals based on your answers above. Be as specific as you can.
Answer: I will reread the paper and also continue my code because I might end up doing something very similar for my final presentation. Additionally, the data sets in these papers aren't public so I'll contact the professor on advice to get data sets
