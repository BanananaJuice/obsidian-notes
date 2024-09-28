## Summary

A classification tree is a type of [[Decision Trees]] that segregates data into different categories

-------------------------------------------------------------------

## Related Sections/Pre-Reading


-------------------------------------------------------------------
## Content: Building Data into a Classification Tree

### Issue
The issue with turning data into a classification tree is how to evaluate which different features you should start with in order to categorise your data correctly. ie which question should be asked in which order in the classification tree

### Example
Below is an example of a decision tree built from data. We will now work backwards using statistical methods to decide in which order the questions should be asked to create the classification tree. For this we use Gini Impurity
![[Assets/Building_Classificatio_Tree_Example.png]]

### Gini Impurity
Gini Impurity is a statical method used to quantify the #Purity  of a feature in predicting a specific class. Therefore you would use the feature with the lowest Gini Impurity as the #RootNode

![[Assets/Gini_Impurity_Calculation.png]]


### Terminology
- **Purity** in a decision tree refers to how much a group of data points at a node belong to the same class. A node is considered  if all the data points in it are of the same class. The more mixed the classes are in a node, the less pure it is. Decision trees aim to create nodes that are as pure as possible, meaning each node ideally contains data points from just one class. #Purity

#GiniImpurity
#education 