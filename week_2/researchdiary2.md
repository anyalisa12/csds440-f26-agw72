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
Answer: This week I worked with influence functions on a 1D CNN which is a main part of my project. 1D CNNs are an easy approach to understanding this concept especially that they process sequential data and instead of 2d image filters which I think are more complex. ID CNNs have kernels which are filters sliding along one axis and this way I can easily apply an influence function. 

2. List all resources you have read or looked at this week, along with the time you
spent on each one (to the nearest 1/2 hour is enough). For web pages, blog posts,
videos etc, provide links and titles. For papers, provide links and citations. For
code written, provide a Jupyter notebook in the Week_n folder and list the file
name (as a link) here. For AI tools, provide a transcript of your session in a
separate file in the Week_n folder, and list the file name (as a link) here. The
transcript file can be a text file or pdf. Do *not* link to chat sessions directly.

Answer: I spent 2 hours reading the paper " Interpreting the decisions of CNNs via influence functions" and I also read one more paper for 1.5 hours, this paper was about how CNNs were used in fault diagnosis which is a bit tangent to my blackbox predictions bust because the focus of my paper is on prediction influence, I found the paper " Federated Learning for Privacy-Preserving
Collaboration " very helpful because it showed how a 1D CNN was used to improve the predictions of fault analysis for a bearing problem where they used the CWRU bearing data set which is a public data set. And then another set of 2 hours on a separate date writing a simple python program incoporating an influence function in a 1D CNN 

3. Summarize what you have learned **this week** from the resources above. Be
clear, detailed and precise. It is ok to be uncertain about the content. Do **not**
copy/paste content from any resource.
Answer: From the paper " Interpreting the decisions of CNNs via influence functions", I learned that deep learning models when performing class prediction they have to have loss functions and in this specific paper influence  scores were obtained for different images for the class prediction in this CNN. So influence scores were used to find how much one client's training set affected the model's prediction for a specific image.

4. Describe any new ideas you may have had as you were studying the resources, and
if you did any follow ups to investigate these ideas.
Answer: Influence functions have mostly been used in statistics but when thinking of deep learning applications, these functions follow a similar path and can offer useful information by explicitly finding how a change in a singular point affects the estimator and maps the prediction. When working with a CNN for my code I used the CWRU bearing data and influence functions basically helped me classifiy if the faults in the bearing were overload of bearing or unlubricated causes and it was able to use the signals from th training examples to find which had a bigger effect on a particular classification.


6. If you implemented/ran any code or algorithms from the resources or while
investigating any new ideas, describe what you did. Link to a jupyter notebook in
your Week_n folder showing the runs. You may also include python files containing
code in your Week_n folder. If so, their content should be described here. If you
forked another repo or imported pre-built code, please provide a link. If an AI
tool wrote part of the code, please provide a session transcript in the Week_n
folder and link to it here. If any part of the code did not run or did not behave
as expected, describe your best guess why and possible fixes.
Answer:
7. Summarize any specific points of confusion, uncertainty or difficulty from your
reading or implementation that arose from your readings or implementations this
week. This can partly overlap with your answer (3).
Answer:
8. List specific goals you would like to accomplish for next week and action items
aligned with these goals based on your answers above. Be as specific as you can.
Answer:

