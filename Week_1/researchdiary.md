Research Diary Template
---------------------------

Answer all questions. For those which do not apply write "Not Applicable." Place the completed diary and all other resources indicated below in a folder "Week_n" in your cwru-courses repository, where n is 1 to 5. I expect the diary to show clearly that you have spent at least 6 hours on this work (including the time spent preparing this diary).

1. Briefly summarize your knowledge of the area you are researching as of last week, and your plans for the current week from Q7 of your last diary. If this is the first diary write "Not Applicable."

Answer:

2. List all resources you have read or looked at this week, along with the time you spent on each one (to the nearest 1/2 hour is enough). For web pages, blog posts, videos etc, provide links and titles. For papers, provide links and citations. For code written, provide a Jupyter notebook in the Week_n folder and list the file name (as a link) here. For AI tools, provide a transcript of your session in a separate file in the Week_n folder, and list the file name (as a link) here. The transcript file can be a text file or pdf. Do *not* link to chat sessions directly. 

Answer: I first read my assigned paper for 3 hours in the Kelvin Smith library; Understanding Black-box Predictions via Influence Functions and then I met my classmate in CSDS 440 who is a Computer science major in order to discuss a few things I did not understand (30 minutes).I then read another paper on influence functions in order to better understand them; https://www.jmlr.org/papers/volume9/debruyne08a/debruyne08a.pdf. Thereafter, I used CHATGPT to answer a few questions on concepts that I did not understand.

3. Summarize what you have learned **this week** from the resources above. Be clear, detailed and precise. It is ok to be uncertain about the content. Do **not** copy/paste content from any resource.

From the paper understanding Blackbox predictions via Influence functions, I learned how influence functions work and how they find the specific training points which cause a specific prediction.  


4. Describe any new ideas you may have had as you were studying the resources, and if you did any follow ups to investigate these ideas.

Answer: The counterfactual concept in influence functions, they work backwards in a way that they try to imagine the scenario when a certain point isn't there. They answer the question of how the removal of this point would affect the prediction made. From my second reading https://www.jmlr.org/papers/volume9/debruyne08a/debruyne08a.pdf ;I learned how influence functions can be used to understand the effects of outliers on an estimator. I followed up on this investigation through a chat with CHATGPT cited in my resources and I was able to conclude that influence functions are rarely used for outlier estimators but rather with data that is within range in order to understand how removal of specific points can affect the model directly.

5. If you implemented/ran any code or algorithms from the resources or while investigating any new ideas, describe what you did. Link to a jupyter notebook in your Week_n folder showing the runs. You may also include python files containing code in your Week_n folder. If so, their content should be described here. If you forked another repo or imported pre-built code, please provide a link. If an AI tool wrote part of the code, please provide a session transcript in the Week_n folder and link to it here. If any part of the code did not run or did not behave as expected, describe your best guess why and possible fixes.

Answer: Not Applicable because it was my first week of reading and I will implement code in my next week's tasks. This week I focused on understanding influence functions

6. Summarize any specific points of confusion, uncertainty or difficulty from your reading or implementation that arose from your readings or implementations this week. This can partly overlap with your answer (3).

Answer: I am confused about how finding the points in influence function from training data can directly translate to better predictions for our testing data. And since for adversarial network models, they place less importance to having a small number of points, doesn't this affect the models performance? Since we need more points to have a better performing model and a more secure model in the real world application of ML models 

7. List specific goals you would like to accomplish for next week and action items aligned with these goals based on your answers above. Be as specific as you can.

Answer: I plan on working on code with a very simple 1D CNN to first code an influence function and i will use kernels based regression to see how this can influence the model being trained. And after I understand how influence functions operate then I will read more about black box predictions.
