

**Power System Stability Assessment: A Deep Learning Approach**

Simran

With the integration of communication technologies and advanced metering infrastructures in the

traditional power system, the smart power grid has been recognised as an important form of

cyber-physical system (CPS). They play an important role in reliable and efficient energy

production and management. However, its interoperability and dependency on communications

networks increase the system's vulnerability to faults, thus bringing up new challenges in system

monitoring and control. Since such failures may lead to catastrophic events, it is highly important

to investigate the effect of faults and disturbances on them. Therefore, we aim towards shifting

the focus to real-time monitoring and control of smart power grids to eventually mitigate the

effect of faults and enhance the security margin of the system.

**Objectives:**

Considering the nature of the problem to be investigated, we propose the following objectives:

\1. Take the opportunity to assess the influence of deep learning architecture (number and

size of hidden layers), number of epochs and the relevance of dataset augmentation.

\2. We aim to work on a modified FNN(Feedforward Neural Network) for real-time

assessment of transient stability(TS) with prediction capability before fault clearance.

\3. We wish to focus on a comprehensive assessment through numerous fault scenario

simulations, including various fault duration, fault location, and load profile intervals.

**Introduction:**

Proper monitoring and control of the smart grid are highly dependent on the transient stability

assessment (TSA). Effective TSA can provide system operators with insightful information on

stability statuses and causes under various contingencies and cyber-attacks. In our project, we

work on a real-time stability condition predictor based on a feedforward neural network. We plan

to use the conjugate gradient backpropagation algorithm for training. We believe that by

real-time assessment of the network features based on the minimum redundancy maximum

relevance algorithm, this method can successfully predict transient stability and out of step

conditions for the network and generators, respectively.

The proposed method used in this project using the Feedforward Neural Network , helps in

providing a TS prediction which would thereby help in predicting the TS condition before the

fault clearance, thus significantly saving time in control actions/operations by the operator .





**Renewable Energy Sources and Smart Grids:**

The ascent of renewable energy sources provides the global community with a much demanded

alternative to traditional, finite and climate-unfriendly fossil fuels. However, their adoption poses

a set of new paradigms, out of which two interrelated aspects deserve particular attention:

● Prior to the rise of renewable energy sources, the traditional operating ecosystem

involved few production entities (sources) supplying energy to consumers over

unidirectional flows. With the advent of renewable options, end users (households and

enterprises) now not only consume energy but have the ability to produce and supply it -

hence a new term to designate them, '**prosumers**'. As a result, energy flow within

distribution grids - '**smart grids**' - has become **bidirectional**;

● Despite the increased flexibility brought in by the introduction of renewable sources and

the aforementioned emergence of 'prosumers', the management of supply and demand in

a more complex generation / distribution / consumption environment and the related

economic implications (particularly the decision to buy energy at a given price or not)

have become even more challenging.

**Modelling grid stability:**

In a smart grid, consumer demand information is collected, centrally evaluated against current

supply conditions and the resulting proposed price information is sent back to customers for

them to decide about usage. As the whole process is time-dependent, dynamically estimating

**grid stability** becomes not only a concern but a major requirement.

Put simply, the objective is to understand and plan for both energy production and/or

consumption disturbances and fluctuations introduced by system participants in a dynamic way,

taking into consideration not only technical aspects but also how participants respond to changes

in the associated economic aspects (energy price).

Simulations are run on a model **4-node star** architecture, comprising one power source (a

centralised generation node) supplying energy to three consumption nodes.

The model takes into consideration inputs (features) related to:

● the total **power balance** (nominal power produced or consumed at each grid node);

● the response time of participants to adjust consumption and/or production in response to

price changes (referred to as "**reaction time**);

● energy **price elasticity**.





**The dataset:**

The dataset selected is the Electric Grid Stimulated Data from the UCI Machine learning

Repository.

<https://archive.ics.uci.edu/ml/datasets/Electrical+Grid+Stability+Simulated+Data+>

The dataset chosen for this machine learning exercise has a synthetic nature and contains results

from simulations of the local stability analysis of the 4-node star system for grid stability

implementing the Decentral Smart Grid Control Concept.

The dataset has **60,000 observations**. It contains **12 primary predictive features** and one

dependent variable.

**Predictive features**:

\1. 'tau1' to 'tau4': the reaction time of each network participant, a real value within the range

0.5 to 10 ('tau1' corresponds to the supplier node, 'tau2' to 'tau4' to the consumer nodes);

\2. 'p1' to 'p4': nominal power produced (positive) or consumed (negative) by each network

participant, a real value within the range -2.0 to -0.5 for consumers ('p2' to 'p4'). As the

total power consumed equals the total power generated, p1 (supplier node) = - (p2 + p3 +

p4);

\3. 'g1' to 'g4': price elasticity coefficient for each network participant, a real value within the

range 0.05 to 1.00 ('g1' corresponds to the supplier node, 'g2' to 'g4' to the consumer

nodes; 'g' stands for 'gamma');





**Dependent variables**:

\1. 'stabf': a categorical (binary) label ('stable' or 'unstable').

**Libraries used:**

Along with traditional libraries imported for tensor manipulation, mathematical operations and

graphics development, three scikit-learn modules (StandardScaler as a scaler, confusion\_matrix

as the model performance metric of choice and KFold as the cross validation engine) and two

Keras deep learning objects (Sequential and Dense) are used in this exercise.

**Model definition:**

**What is a feedforward neural network and how does it work ?**

In its most basic definition, a feed forward neural network is a single layer perceptron.The

feed-forward model is the simplest type of neural network because the input is only processed in

one direction..In this model, a sequence of inputs enter the layer and are multiplied by the

weights.If the sum of the values is more than the predetermined threshold,the output value is 1,

and if the sum of these values is less than the predetermined threshold ,the output value is -1.The

neural network compares the outputs of its nodes with the desired values using a property known

as the delta rule, allowing the network to alter its weights through training to create more

accurate output values. This training and learning procedure results in gradient descent.

The artificial neural network (ANN) architecture reflects a sequential structure with:

● one input layer (12 input nodes);

● three hidden layers (24, 24 and 12 nodes, respectively);

● one single-node output layer.

As features are numerical real numbers within ranges, the choice of 'relu' as the activation

function for hidden layers seems straightforward. Similarly, as this is a logistic classification

exercise, where the output is binary ('0' for 'unstable', '1' for 'stable', following map coding), the

choice of 'sigmoid' as activation for the output layers seems obvious.

Compilation with 'adam' as optimizer and 'binary\_crossentropy' as the loss function follow the

same logic. The fitting performance will be assessed using 'accuracy' as the metric of choice.





**Results :**

The results were showcased using the Confusion Matrix table. A confusion matrix is **a table that**

**is used to define the performance of a classification algorithm**. A confusion matrix visualises

and summarises the performance of a classification algorithm.The accuracy from the confusion

matrix table was found to be 97.73%.

**Conclusion:**

Specific aspects of this deep learning exercise demand special attention:

\1. Deep learning proved to be an outstanding prediction tool for this particular application.

Even considering that the dataset is well behaved and needs no significant preprocessing,

the **high accuracies** obtained on the testing set confirm that a deep learning model may

be safely considered. It would then be up to a smart grid operator to confirm if the

accuracy level obtained with deep learning would suffice in practical terms (live

network);

\2. An **increased number of epochs** considered during fitting also plays a major role. It is

evident that the more the model is exposed to the training set, the better the prediction

accuracy;





**References :**

[**https://arxiv.org/abs/1508.02217**](https://arxiv.org/abs/1508.02217)

[**https://ieeexplore.ieee.org/document/8587498**](https://ieeexplore.ieee.org/document/8587498)

[**https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/iet-stg.2019.0191**](https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/iet-stg.2019.0191)

