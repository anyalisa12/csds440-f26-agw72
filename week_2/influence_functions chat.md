
An influence function is a concept from statistics that measures how much an estimator changes when a single observation is slightly perturbed or added to the data. It is a fundamental tool in robust statistics and also appears in modern machine learning.
Intuition
Imagine you've calculated the average height of 1,000 people. Now you add one extra person who is 8 feet tall. The average changes slightly.
The influence function asks:
"How sensitive is my estimate to one particular data point?"

If a small change in one observation causes a large change in the estimate, that observation has high influence.
Formal definition
Suppose an estimator computes a parameter \(T(F)\) from a population distribution \(F\).
Now contaminate the distribution by adding a tiny amount of probability mass \(\varepsilon\) at a point \(x\):
\[
F_\varepsilon = (1-\varepsilon)F + \varepsilon\delta_x,
\]
where \(\delta_x\) is a point mass at \(x\).
The influence function is
\[
\mathrm{IF}(x;T,F)
=
\lim_{\varepsilon\to0}
\frac{T(F_\varepsilon)-T(F)}{\varepsilon}.
\]
It is essentially the derivative of the estimator with respect to contamination at \(x\).
Example: Sample mean
For the population mean,
\[
T(F)=\mu.
\]
The influence function is
\[
\mathrm{IF}(x)=x-\mu.
\]
This tells us:
- observations near the mean have little influence,
- observations far from the mean have large influence.
This is why the sample mean is not robust to outliers.
Example: Median
The median has a bounded influence function (under mild assumptions). This means even an extremely large outlier cannot arbitrarily change the estimate.
This explains why the median is much more robust than the mean.
In machine learning
Influence functions are used to answer questions like:
- Which training examples most affected this prediction?
- Which mislabeled training points are hurting performance?
- What happens if I remove one training example?
Instead of retraining the model many times, influence functions approximate the effect using derivatives of the loss and the inverse Hessian of the training objective.
For a model parameter estimate \(\hat\theta\), the approximate change from upweighting a training point \(z_i\) is
\[
\frac{d\hat\theta}{d\varepsilon}
=
-
H^{-1}\nabla_\theta L(z_i,\hat\theta),
\]
where:
- \(L\) is the loss,
- \(\nabla_\theta L\) is its gradient,
- \(H\) is the Hessian of the total training loss.
This allows researchers to identify influential training examples without retraining the model from scratch.
Summary
An influence function quantifies the local sensitivity of an estimator to an individual observation.
- In robust statistics: it measures resistance to outliers.
- In classical statistics: it helps analyze estimators and derive asymptotic properties.
- In machine learning: it estimates how individual training samples affect model parameters and predictions.
In essence, you can think of the influence function as answering the question:
"If I nudged this one data point a tiny bit, how much would my estimate change?"














how do influence functions analyse the effect of outliers and is it only outliers that get analysed












No. Influence functions are not only used to analyze outliers. Outliers are just one of the most intuitive applications.
1. How influence functions analyze outliers
Suppose you have data:
\[
2,\;3,\;4,\;5,\;6
\]
and you're estimating the mean:
\[
\bar{x}=4.
\]
Now consider an outlier \(x=100\).
For the mean, the influence function is
\[
IF(x)=x-\mu.
\]
So for \(x=100\):
\[
IF(100)=100-4=96.
\]
That's very large, meaning that observation has a large influence on the estimated mean.
Compare that with \(x=5\):
\[
IF(5)=5-4=1.
\]
So \(x=5\) has very little influence.
The important idea is:
\[
\boxed{\text{Large influence function value} \Rightarrow
\text{the observation can strongly affect the estimator}}
\]
2. Why this is useful for outliers
An outlier is an observation that is unusual relative to the rest of the data.
For many estimators, unusual observations have large influence.
For example:
\[
\text{Normal point} \rightarrow \text{small influence}
\]
\[
\text{Extreme point} \rightarrow \text{large influence}
\]
This lets you study questions such as:
"If this observation were given slightly more weight, how much would my model's estimate change?"

You don't necessarily have to remove the observation. You can measure its influence first.
3. But influence ≠ outlier
This distinction is important.
An outlier is about the observation itself:
\[
\boxed{\text{"Is this observation unusual?"}}
\]
An influence function is about the effect of that observation:
\[
\boxed{\text{"How much does this observation affect my estimator?"}}
\]
Those are not the same thing.
You can have:
Observation	Is it unusual?	Influence
Typical observation	No	Low
Extreme observation	Yes	High
Extreme observation	Yes	Potentially low
Typical-looking observation	No	Potentially high


So an observation can be unusual without necessarily having a huge effect on the particular estimator you're studying.
4. Influence functions can analyze much more than outliers
They can be used to study the effect of any individual observation or small perturbation.
For example:
Data cleaning
"Which training examples have the greatest effect on my model?"

Mislabeled data
"What happens to my model if this incorrectly labeled example is removed?"

Fairness
"How much does changing the weight of observations from a particular group affect the prediction?"

Robustness
"How sensitive is my estimator to small changes in the data?"

Machine learning
"Which training examples are responsible for this particular prediction?"

Data removal
"What happens to the model if I remove this training point?"

5. Connecting this to your earlier Hessian question
This is especially relevant to what you were asking about upweighting a training example and then removing it.
Suppose your training set contains an example \(z\). You increase its weight by a tiny amount \(\epsilon\).
The influence function estimates:
\[
\frac{d\hat{\theta}}{d\epsilon}
\]
which means:
How does the learned model parameter \(\hat{\theta}\) change when I slightly increase the importance of \(z\)?

Then, approximately,
\[
\hat{\theta}_{\text{after removing }z}
\approx
\hat{\theta}
-
\frac{1}{n}
\frac{d\hat{\theta}}{d\epsilon}.
\]
So in machine learning, influence functions can be used to identify which training examples are most responsible for a model's parameters or a particular prediction.
That's why you'll often see influence functions discussed in papers about data attribution, mislabeled examples, outliers, data poisoning, and model debugging.
The key distinction to remember:
\[
\boxed{\text{Outlier detection asks: "Is this point unusual?"}}
\] 
