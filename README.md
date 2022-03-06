This lab was created  by Tomás de la Rosa , professor from mIA-X master's degree at BME Institute. It necessarily needed to be programmed in Python.

Check out his LinkedIn profile.

<a href="https://www.linkedin.com/in/tom%C3%A1s-de-la-rosa-3b593827/" target="_blank"><img alt="LinkedIn" src="https://img.shields.io/badge/linkedin-%230077B5.svg?&style=for-the-badge&logo=linkedin&logoColor=white" /></a> 

### Instructions

The goal of this lab is to use machine learning techniques to build models that allow to recognize patterns of technical analysis within a series of prices. In its simplest form these models can be approached as a binary classification task in which the model is capable of identify:

1. Positive class: There is a pattern in a time window. Example a double bottom pattern.
2. Negative class: The pattern of interest does not exist in the indicated time window.

An example of a positive class would be:

![alt text](https://a.c-dn.net/c/content/dam/publicsites/igcom/uk/images/ContentImage/Double%20bottom.png)


The lab should be done in Python notebooks using the sklearn library. It can be used any other library deemed necessary.

### 1st part


In this version it is required to generate a model that classifies a double bottom pattern and show the results that show that said model is better than randomness. Optionally, the student can choose a different technical pattern that is of interest to you. The suggested steps are:

1. Label the temporary windows of the IBEX as positive and negative examples with the notebook of labeling. It is suggested to have at least 60 plots.
2. Extract the OHLC strings from the labeled windows.
3. Generate features that are considered interesting to recognize the pattern from the data of the temporary window (see comments below).
4. Train a model of those seen in class by separating the data in train/test.
5. Report the evaluation results that can be included in a notebook with the code for generate them. The evaluation should include:
  - A confusion matrix
  - Accuracy and AUROC results
  - A ROC curve

Regarding the generation of characteristics, it is recommended to generate simple functions that calculate values that help to distinguish some series from others, regardless of the pattern that is being searched for. What the windows would have a different price scale, it is necessary that the characteristics are normalized.
Some examples can be:

- Number of days that pass between the maximum and the minimum of the window
- If the maximum or minimum occurs first
- Number of times in the window that a certain threshold is reached


### 2st part

In this part, it is requested to address the problem as a multiclass classification so that they can be recognized at the same time several technical figures. A simple scheme would be to have, for example, a double bottom, a double top and without pattern. Suggested tasks are:

1. Carry out steps 1 to 3 of the first iteration, but taking into account the required considerations for the multiclass problem.
2. Train classifiers using 3 different algorithms, and choose the best one based on accuracy estimated with cross validation.
3. Report the evaluation of the best model on a separate test set. Here should be included precision and sensitivity, by class and in their micro-average and macro-average versions.
4. Use the model to identify 5 patterns of each class in the EUROSTOXX historical series.

For example, you can iterate over the temporary windows and choose the most reliable ones in the prediction of each class.

### 3rd part

In this part the problem will be approached from a semi-supervised learning approach. Since labeling is a manual and relatively slow process, we propose to label a larger training set using a co-training algorithm. The suggested steps are:

1. Use a set labeled in the previous parts and develop an independent set of new features. If more than 5 characteristics are available, they could be divided into 2 sub-sets.

2. Generate a set S0 to be labeled by drawing random windows from the set.

3. Train two models, one with each set of features, and label a subset S' according to the class with the highest confidence in both models. Assume now, that S’ labeled together with the initial labels is the new training set, and repeat the process for a number small number of iterations.

4. Train a meta-classifier with the final S0 dataset and report the results comparing them with the results obtained in the previous version (whether starting from iteration 1 or from iteration 2).


### Deliverable

The submitted file must contain:

1. The notebooks that generate the models and report the results of the practice.
2. The series of manually labeled windows, saved in CSV format.
3. A subfolder with the charts predicted for EUROSTOXX (last section of the second part).

