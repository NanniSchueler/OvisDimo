# Machine Learning Inroduction
## A Short Introduction to the used Algorithms

_Machine Learning_, _Artificial Intelligence_ and _Deep Learning_ have been prominently used buzzwords over the last decade. Concurrently, the differences between these terms have blurred and they sometimes have been used synonymously. 

Before we go into detail about specific algorithms and their respective strengths and drawbacks as well as their recommended field of application, we would like to define these general terms and give an understanding of what are realistic goals and expectations when working with these advanced algorithms.

The _Singapore Computer Society_ defines Artificial Intelligence (abbr. **AI**) as "the development of smart systems and machines that can carry out tasks that typically require human intelligence"[^1]. AI is a more abstract concept and can combine multiple problem-solving mechanisms within one system. Machine Learning (abbr. **ML**) algorithms hence are a subsection of an AI system and can draw conclusions and new information from data as well as make decisions based on previously observed and learned patterns. The field of ML algorithms then further splits into _Deep Learning_ (abbr. **DL**) and _Shallow Learning_, although the latter is usually just referenced by the general term of Machine Learning. The main difference here is that in foundational Machine Learning, the features, i.e. the data columns, have to be pre-defined by the user. In Deep Learning the system, typically a complex artificial neural network, will autonomously select the features to determine an outcome. Examples of this are image processing tasks, where a neural network is presented with a plethora of pictures of cats and needs to extract and conclude what "a cat is made of" to identify one in a picture. (Shallow) ML algorithms, on the other hand, can only operate on fixed features, such as "height", "weight", "has whiskers" or "fur color" for a possible prediction. If the training data set already has labels, such as _cat_ or _dog_ in this example, i.e. the resulting possible outcomes are already defined, the algorithms used are called _supervised learning algorithms_. In the case of an unknown distribution of labels or groups in the data _unsupervised learning algorithms_ separate the data set into partitions, placing "similar" data points into one group, then called a cluster, and maximizing the difference between data points in different groups. 

A simplified overview of the relations of all these terms is depicted here:

![AI vs ML](AdditionalFigures/AIvsML.png)

## Supervised Learning Algorithms 
In (Shallow) Machine Learning, supervised learning algorithms describe a paradigm that requires labeled data as input to generalize and summarize, hence _learn_ from. The so-called labels represent the groups or categories the data should be separated into and that are of interest to the user. The algorithms then use various steps of calculations to _learn_ how to differentiate the given groups. This means, that the dataset that is used to train the algorithm, the so-called _train set_, needs to be carefully and diligently selected and manually labeled by experts to maximize the effectiveness of the following predictions. Having learned what features or measurements most contribute to the affiliation of a data point to a certain group, the algorithm can then categorize and sort unknown data into the learned groups. 

Many supervised learning algorithms are mathematically easy to understand and can already give promising results in these classification tasks at hand.

In the following subsections, a selection of commonly used supervised learning algorithms will be explained and tested on our use-case of identifying and predicting the sex of sheep given only the measurements of their skeletal remains.

### $k$-Nearest Neighbors
The $k$-nearest neighbor algorithm (abbr. $k$NN) is a very straightforward supervised learning algorithm but oftentimes strikingly effective in terms of classifying data with only a small number of possible groups and a relatively small data set. As both of these descriptions are accurate for this specific case, this algorithm is an evident first pick. The main idea of the algorithm can be summarized as the following: Given a set of labeled data points in a $n$-dimensional space, the new point is classified by calculating the spatial distance to every other point in the set using a Euclidean distance function. 
The Euclidean distance in $n$-dimensional space is defined as the square root of the sum of all pairwise subtracted squares: 
$$
\sqrt{\sum_{i=1}^{n} (p_i - q_i)^2}
$$
where $p$ and $q$ is the pair of points and $n$ the dimensionality of the data set. 

The name-giving parameter $k$ then determines how many "neighbors", i.e. spatially closest points, are to be considered. The most prominently present label in this neighboring subset of data points determines the label of the new point. A graphical example is given in the Figure below. The data set consists of a total of 12 points, 5 labeled as class _pink_ (triangle) and 7 labeled as _blue_ (circle). The new point (grey star) has to be classified as one of these two classes. When parameter $k$ is chosen to be $4$, the point would be classified as _pink_, because out of its $4$ nearest neighbors, $3$ of them are part of the class _pink_. If $k$ is set to $11$, the _blue_ class has the majority of the $11$ neighbors and the point would be assigned to the _blue_ class.

![kNN](AdditionalFigures/knn.png)

$k$NN is an algorithm with strengths in its simplicity and robustness, especially in very small data sets. Its only parameter $k$, needs to be chosen concerning the size of the already labeled training set. When $k$ is set too small, the algorithm becomes prone to outliers and might misclassify the new data points. When $k$ is chosen to be big, the algorithm loses its effectiveness as simply the majority of the label in the data set is always chosen as the predicted association. Another drawback of $k$NN is its limitation in the number of dimensions and the number of labels or groups. As Euclidean distance differences vanish in high dimensionality (this is one aspect of the effects of the so-called _curse of dimensionality_), accurately localizing one point's neighbors gets harder in a high dimensional space. With a high number of different labels, i.e. classes to divide the data set in, a similar problem arises, as multiple groups might be present most prominently in the neighboring points, resulting in a random pick by the algorithm.


----
[^1]: ToDo.