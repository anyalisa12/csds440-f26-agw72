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

Answer: Last week, i started researching what python library I would use to make blackbox predictions using CNNS and if I could use autoenconders in a latent space. I have read about CNNs and I have written code which is shown in section 6. I will be implementing autoencoders which I studied from chapter 2 of the textbook. 

2. List all resources you have read or looked at this week, along with the time you
spent on each one (to the nearest 1/2 hour is enough). For web pages, blog posts,
videos etc, provide links and titles. For papers, provide links and citations. For
code written, provide a Jupyter notebook in the Week_n folder and list the file
name (as a link) here. For AI tools, provide a transcript of your session in a
separate file in the Week_n folder, and list the file name (as a link) here. The
transcript file can be a text file or pdf. Do *not* link to chat sessions directly.

Answer: I read the textbook for 3hours to finish chapter to understand autoencoders. An encoder network compresses high dimensional input data into low dimensiona embedding vectors. I used chatGPT to brainstorm how I would use an autoencoder and I found that  if I trained an autoencoder using normal bearing vibration signals, it may reconstruct normal signals well but produce larger reconstruction errors for unfamiliar fault patterns.

3. Summarize what you have learned **this week** from the resources above. Be
clear, detailed and precise. It is ok to be uncertain about the content. Do **not**
copy/paste content from any resource

Answer:  From the textbook, I read about keras and tensor flow. Keras are a high level python Library that offer useful building blocks for building more complex applications in Machine Learning models. For my project, I thought Keras were good but I read more on Tensorflow library and saw it's application with influence functions and decided to use it instead 

5. Describe any new ideas you may have had as you were studying the resources, and
if you did any follow ups to investigate these ideas.
Answer: If I am coding and auto encoder, i don't technically need a decoder and encoder network functioning separately because the enconder would compress the input and the decoder would decompress. However the autoencoder combines them both and is able to do both compression of input and decompression of my output

6. If you implemented/ran any code or algorithms from the resources or while
investigating any new ideas, describe what you did. Link to a jupyter notebook in
your Week_n folder showing the runs. You may also include python files containing
code in your Week_n folder. If so, their content should be described here. If you
forked another repo or imported pre-built code, please provide a link. If an AI
tool wrote part of the code, please provide a session transcript in the Week_n
folder and link to it here. If any part of the code did not run or did not behave
as expected, describe your best guess why and possible fixes.
Answer: Yes, I learned how to use tensorflow and CNNS in python

#using CNNS (convolutional networks)
from tensorflow.keras.layers import Conv2D, BatchNormalization, LeakyReLU, Dropout

input_layer = Input(shape=(64,64,1))

conv_layer_1 = Conv2D(
    filters = 2
    , kernel_size = (3,3)
    , strides = 1
    , padding = "same"
    )(input_layer)

#using keras for the network
input_layer = Input(shape=(32,32,3))

conv_layer_1 = Conv2D(
    filters = 10
    , kernel_size = (4,4)
    , strides = 2
    , padding = 'same'
    )(input_layer)

conv_layer_2 = Conv2D(
    filters = 20
    , kernel_size = (3,3)
    , strides = 2
    , padding = 'same'
    )(conv_layer_1)

flatten_layer = Flatten()(conv_layer_2)

output_layer = Dense(units=10, activation = 'softmax')(flatten_layer)

model = Model(input_layer, output_layer)

# batch normalization

# putting it all together
input_layer = Input((32,32,3))

x = Conv2D(filters = 32, kernel_size = 3
	, strides = 1, padding = 'same')(input_layer)
x = BatchNormalization()(x)
x = LeakyReLU()(x)

x = Conv2D(filters = 32, kernel_size = 3, strides = 2, padding = 'same')(x)
x = BatchNormalization()(x)
x = LeakyReLU()(x)

x = Conv2D(filters = 64, kernel_size = 3, strides = 1, padding = 'same')(x)
x = BatchNormalization()(x)
x = LeakyReLU()(x)

x = Conv2D(filters = 64, kernel_size = 3, strides = 2, padding = 'same')(x)
x = BatchNormalization()(x)
x = LeakyReLU()(x)

x = Flatten()(x)

x = Dense(128)(x)
x = BatchNormalization()(x)
x = LeakyReLU()(x)
x = Dropout(rate = 0.5)(x)

x = Dense(NUM_CLASSES)(x)
output_layer = Activation('softmax')(x)


7. Summarize any specific points of confusion, uncertainty or difficulty from your
reading or implementation that arose from your readings or implementations this
week. This can partly overlap with your answer (3).
Answer: I am still confused about loss functions but they will be covered in class nexweek according to the syllabus.

8. List specific goals you would like to accomplish for next week and action items
aligned with these goals based on your answers above. Be as specific as you can.
Answer: I am going to write code of a CNN and an influence functions and read one more paper on black box predictions and how my results can be represented

