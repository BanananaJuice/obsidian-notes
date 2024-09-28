## Summary

AdaBoost algorithm, short for Adaptive Boosting, is a Boosting technique used as an Ensemble Method in Machine Learning

The principle behind Ada boosting algorithms is that we first build a model on the training dataset and then build a second model to rectify the errors present in the first model. This procedure is continued until and unless the errors are minimized and the dataset is predicted correctly.

The main concepts from AdaBoost are:
1. Combines a lot of weak learners to make classifications
2. Each decision tree created has a different weighting of how it contributes to the overall classification
3. Decision trees are created sequentially and 'learn' from the previous decision trees mistake


-------------------------------------------------------------------
## Related Sections/Pre-Reading

- [[Random Forest]]
- [[Classification Trees]]
- [[Bias vs Variance]]

-------------------------------------------------------------------
## Content

### 1. Creation of your first weak learner

The first step in ada-boosting is creating your first weak learner. For this example, we will be using decision trees as our classifier.

We will look at our dataset and determine which feature will be the initial best classifier of the data, i.e. the feature that produces the lowest #GiniImpurity .

From this feature, we will create our first weak learner or #stump.

### 2. Setting the initial weight for all the rows in your data.

Weight refers to how much we emphasise the correctness in classification of each row in the data. For the initial stump, we say that each row is equally important and therefore assign an equal sample weight of 1/number of rows

### 3. Determining the error of the weak learner

The next step is to determine the error rate of the weak learner. This is calculated as the sum of all the eights of the items that the learner incorrectly classified. Therefore a value of 0 will be that all the values were correctly classified and 1 being everything was incorrect

### 4. Calculating the amount of say the weak learner has

The amount of say means how much this weak learner contributes to the overall assessment at the end of the model when classifying data. 

The amount of say is proportionate to the error the stump has. The lower the error the more say a stump will have in the final classification.

Say is calculated as follows

$$
\text{amount of say} = \frac{1}{2}log(\frac{1-\text{Total Error}}{\text{Total Error}})
$$

### 5. Calculating the New Weights

Now that we are done creating the first model. We will update our weighting of the 1population items. This is the part that makes this boosting technique adaptive or learning from its previous models.

Incorrectly classified items will be weighted higher and therefore more emphasis is put on the second model to correctly classify them.

The weight is calculated as follows
$$
\text{new weight} = \text{original weight} \times e^{\text{amount of say}} 
$$
### 6. Rinse and repeat

Ok, finally we have all our new weights and we are ready to start the process from step 1 again. 

The first step again is to now recalculate the #GiniImpurity for all the variables using weighted averages from the sample weights

### 7. Conclusion and classifying

After a given number of repetitions, we will find ourselves with quite a few stumps and their relevant weightings.

Now we will run our testing data down each stump, summing up the weights of the classifiers that vote in either direction.
The classification chosen will be the value that is higher.