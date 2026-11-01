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

Answer: This week I focused on finding essential data sets in the manufacturing area that can suit my study of black box predictions. Because I am passionate about sustainable manufacturing in particular, I looked at the Oakridge Laboratory Data set to find studies that would be of my interest. Even though I am doing ML in this project, I have to emphasize the importance of studying a topic in my field of study. 

2. List all resources you have read or looked at this week, along with the time you
spent on each one (to the nearest 1/2 hour is enough). For web pages, blog posts,
videos etc, provide links and titles. For papers, provide links and citations. For
code written, provide a Jupyter notebook in the Week_n folder and list the file
name (as a link) here. For AI tools, provide a transcript of your session in a
separate file in the Week_n folder, and list the file name (as a link) here. The
transcript file can be a text file or pdf. Do *not* link to chat sessions directly.
Answer: I used the oakridge DOE site to find public data sets. This process of searching took me about 4 hours split in 2 hour sections of library work. I thereafter spent an hour reading about the energy efficiency of different manufacturers and understanding that specific data set. 

3. Summarize what you have learned **this week** from the resources above. Be
clear, detailed and precise. It is ok to be uncertain about the content. Do **not**
copy/paste content from any resource.
Answer:  From the " https://catalog.data.gov/dataset/industrial-assessment-centers-database?" I found that the Industrial Systems and Energy Efficiency Data set was valuable for my project because it had NON-IID data for multiple manufacturers throughout the country with the energy information, the size of the company and these can be parameters that can affect the black box prediction I will be making. I also looked at a 2-D data set from oakridge that studied how different printers, for this data set my vision was to see the image characterization first before using it for a black box prediction. I decided to stick to 1-d DATA and a time series set in particular.

4. If you implemented/ran any code or algorithms from the resources or while
investigating any new ideas, describe what you did. Link to a jupyter notebook in
your Week_n folder showing the runs. You may also include python files containing
code in your Week_n folder. If so, their content should be described here. If you
forked another repo or imported pre-built code, please provide a link. If an AI
tool wrote part of the code, please provide a session transcript in the Week_n
folder and link to it here. If any part of the code did not run or did not behave
as expected, describe your best guess why and possible fixes.
Answer: Yes, I continued my code from week 4 on federated learning as a black box prediction method.
#training clients and testing clients with the federated averaging model
import torch
import torch.nn as nn
import torch.optim as optim
import numpy as np
import random

class CNN1D(nn.Module):
    def __init__(self, input_size, num_classes=48):
        super(CNN1D, self).__init__()

        self.conv1 = nn.Conv1d(1, 16, kernel_size=5, padding=2)
        self.relu = nn.ReLU()
        self.pool = nn.MaxPool1d(2)

        self.conv2 = nn.Conv1d(16, 32, kernel_size=5, padding=2)

        self.fc1 = nn.Linear((input_size // 4) * 32, 128)
        self.fc2 = nn.Linear(128, num_classes)

    def forward(self, x):
        x = self.pool(self.relu(self.conv1(x)))
        x = self.pool(self.relu(self.conv2(x)))

        x = x.view(x.size(0), -1)
        x = self.relu(self.fc1(x))
        x = self.fc2(x)
        return x

def create_clients(X, y, num_clients=5):
    clients = []
    data_per_client = len(X) // num_clients

    for i in range(num_clients):
        start = i * data_per_client
        end = start + data_per_client

        # Non-IID: bias each client to certain classes
        idx = np.where((y % num_clients) == i)[0]
        clients.append((X[idx], y[idx]))

    return clients
#client training 
def client_update(model, data, labels, epochs, batch_size, lr):
    model.train()
    optimizer = optim.Adam(model.parameters(), lr=lr)
    criterion = nn.CrossEntropyLoss()

    dataset = torch.utils.data.TensorDataset(data, labels)
    loader = torch.utils.data.DataLoader(dataset, batch_size=batch_size, shuffle=True)

    for _ in range(epochs):
        for x_batch, y_batch in loader:
            optimizer.zero_grad()
            output = model(x_batch)
            loss = criterion(output, y_batch)
            loss.backward()
            optimizer.step()

    return model.state_dict()

def fedavg(global_model, clients, rounds=10, frac=0.6, epochs=2, batch_size=32, lr=0.001):
    global_weights = global_model.state_dict()

    for r in range(rounds):
        selected_clients = random.sample(clients, int(len(clients) * frac))

        local_weights = []
        sizes = []

        for (data, labels) in selected_clients:
            local_model = CNN1D(input_size=data.shape[2])
            local_model.load_state_dict(global_weights)

            weights = client_update(local_model, data, labels, epochs, batch_size, lr)

            local_weights.append(weights)
            sizes.append(len(data))



6. Summarize any specific points of confusion, uncertainty or difficulty from your
reading or implementation that arose from your readings or implementations this
week. This can partly overlap with your answer (3).

Answer: I was able to get to the averaging step but I still need to understand how individual weights in the training set affect the global weight (prediction) being made by the model. 

7. List specific goals you would like to accomplish for next week and action items
aligned with these goals based on your answers above. Be as specific as you can.

Answer: For next week, because I have worked on the training, I want to advance to my testing set in my code
