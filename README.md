# VideoMemorability
This project tackles the MediaEval Machine Learning Task where it presents various methods to examine the analytical and aesthetic features of a video clip In addition, examines how the combination of those features affects video memorability

## INTRODUCTION
Information and communication technology are
changing swiftly with a major chunk of it being in social
media. The pace at which it is developing is
phenomenal, mobile devices dominate the internet
space by letting them connect to Internet anywhere, at
any time and puts a high-resolution video capturing tool
right in their pocket. The amount of digital content
available online is gigantic and it is almost impossible
to avoid them and besides, not all content is worth
remembering and to tackle this, industry giants are
trying to rope in influential personality to collaborate
with their brands to reach to the masses.[9]

There are plenty of digital content out there and
majority of them being in the advertisement domain
spread across the internet, mainly in social network.
Memorability of the video mainly depends on the
presentation of visual contents and aspects linked to it.
This paper concentrates more on the statistical presence
rather than theoretical or phycological connections
amongst features and memorability. Memorability has
two faces to it, long-term and short-term memorability,
a clear-cut boundary must be drawn between them in
order to predict memorability scores precisely. During
long-term, human brain loses a lot of intricate details
unless they have a relationship linked to it through
hobbies or previous experience.[5][6]It indicates that
predicting long term memorability of a video feature is
far more challenging than short-term as we are losing a
key aspect of personal touch to the features

## Approach
For the algorithm part, I have implemented few
techniques such as Recursive Convolutional Neural
Network (RCNN), Support Vector Regression (SVR),
Linear Regression, Random Forest Regression, Ridge
Regression and finally an ensemble approach using
SVR, Decision Tree’s and Linear Regression as base
classifiers and Rigid Linear Regression as the final
estimator. Main purpose of using multiple models with
various features is to provide comparison between
various approaches.

## Feature Extraction
Three different set of features from the dataset and
certain combination of these features are fed into
models. Selection of the features are mainly focused on
the movement and flow of subjects in the videos. These
features primarily hold information on movement of a
subject through multiple frames. To evade overfitting all
aspects of the frames present in the video is considered
i.e. in certain cases, motion of a subject might be too
short and sudden, even though video might be interesting
but due to unpredictability factor of the subjects it would
be hard to predict the memorability. Here are the
combinations of the features used:
• Captions: Textual features are created manually
which describes the objects or movement of objects in
the video. Here captions are considered as features of
objects present in the videos.
• C3D: C3D feature the final classification layer of the
3D convolutional network, it takes various aspects into
consideration including objects, scenes, movement and
their correlation with each other.[7]
• HMP: HMP contains histogram of motion patterns
for each video which encodes time-based dynamics of
an object related to its action in the video

## Feature Combination
Output predictions of each algorithm is compared
against the ground truth values and Spearman’s score is
calculated, few combinations of features used are as
follows:
Captions + C3D: Textual description are coupled with
object description and their movement.
Captions + HMP: Textual description are combined
with motion patters of an object along with their
temporal dimensions.
C3D + HMP: C3D provides descriptions of objects and
their frequency of occurrence of an object in the video
and this is coupled with motion histogram patters.
All three combined: textual feature with object
description and their movement pattern is considered.

## Model Description
Numerous algorithms were implemented such as
RCNN, SVR, Decision Tree, Random Forest Regressor,
Rigid Regression and an Ensemble of various regressing
algorithms. Since the problem posed is a regression
problem and not a classification problem, predicting
memorability was relatively harder. However, paper
mainly focuses on implementing various techniques and
drawing comparisons between each of them.
Initial dataset is split into Test and Train set with 90:10
ratio respectively. Neural Networks are implemented
using Keras library, architecture contains 3 layers.
Output dimensions of each layer is 30, 25 and 2. Layers
couldn’t be reduced any further because they started
impacting the validation accuracy and Spearman’s
coefficient value started reducing drastically. Scaled
Exponential Linear Unit (Selu) Activation function is
used in every layer, as it performed better with regards
to softplus or Relu functions. Dropout value is set lower
between first and seconds layer, and dropout value
increases as the data travels down the layers. Learning
rate it set to 0.00009 and everything else is at their
default settings, most importantly optimization is done
using Root Mean Square Prop algorithm.
In regression techniques, linear regression is run on
default setup except normalize set to true. SVR and
Rigid Regressing is run with a regularization parameter
to impose penalty. Maximum depth of the Random
Forest decision trees is set to 10.
Final Ensemble approach contains Decision Tree
Regressor, SVR and Linear Regression as used as the
base estimators and are stacked upon each other. Rigid
Regression is implemented as the final estimator and are
run using the same settings mentioned above

## Analysis of the results
Results from the algorithms are described below in
Table 1 which shows Spearman’s score across various
features and algorithms.

![speaman](https://user-images.githubusercontent.com/31949367/81080434-9d401180-8ee8-11ea-8e87-f4add6753fca.PNG)
> Table 1 - Spearman’s score

Captions work best with this problem and when
combined with other two features it provides better
results every time. Linear Regression without
regularization performs poorly.

## Conclusion
Overall short-term memorability scores are higher
when features are combined, and Rigid Regression gives
the best result. As for the long-term memorability, SVR
with all three features provide the best score. Features
provided for this project are pre-extracted from the entire
dataset (8000 videos) and most of the features provide
no direction in terms of memorability according to [4].
In order to improve upon this, scaling up various feature
is necessary to match the human cognition level.

### References
[1] Rachit Dubey, Joshua Peterson, Aditya Khosla,
Ming-Hsuan Yang, Bernard Ghanem, "What Makes
an Object Memorable?," in 2015 IEEE International
Conference on Computer Vision (ICCV), Santiago,
Chile, 13 Dec 2015.
[2] Aditya Khosla, Akhil S. Raju, Antonio Torralba,
Aude Oliva, "Understanding and Predicting Image
Memorability at a Large Scale".
[3] Rachit Dubey, Joshua Peterson, Aditya Khosla,
Ming-Hsuan Yang, Bernard Ghanem, "What Makes
an Object Memorable?," in 2015 IEEE International
Conference on Computer Vision (ICCV), Santiago,
Chile, 13 Dec 2015.
[4] Sathisha Basavaraju, Paritosh Mittal, Arijit Sur,
"Image Memorability: The Role of Depth and
Motion," in 2018 25th IEEE International
Conference on Image Processing (ICIP), Athens,
Greece, 06 September 2018.
[5] Markopoulos, Gerry, "Distinctiveness and memory,"
New York, 2007.
[6] D. Norris, "Short-Term Memory and Long-Term
Memory are Still Different," 2017 May 22.
[7] Tran, D., Bourdev, L.D., Fergus, R., Torresani, L.
and Paluri, M., 2014. C3D: generic features for video
analysis. CoRR, abs/1412.0767, 2(7), p.8.
[8] Raschka, S. and Mirjalili, V., 2019. Python Machine
Learning: Machine Learning and Deep Learning
with Python, scikit-learn, and TensorFlow 2. Packt
Publishing Ltd.
[9] Determining Memorability: How Celebrity
Association Increases Brand Recall:[available
online]https://medium.com/spottedmedia/determining-memorability-how-celebrityassociation-increases-brand-recall-a83ae8fd3f8f
