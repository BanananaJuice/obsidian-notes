## Summary

**CatBoost** (short for "Categorical Boosting") is a machine learning algorithm developed by Yandex, primarily designed for handling **categorical data**. It is an implementation of **gradient boosting** and is often used for classification and regression tasks.

-------------------------------------------------------------------
## Related Sections/Pre-Reading

- [[Decision Trees]]
- [[Classification Trees]]
- [[Bias vs Variance]]
- [[Encoding]]
- [[Random Forest]]
- [[AdaBoost]]
- [[Gradient Boost]]

-------------------------------------------------------------------
## Content

I won't go into detail as to the maths of the categorical boosting model but rather the key principles of it.

Cat boosting uses a fancier version of target encoding to encode all discrete features within a dataset, then performs gradient boosting techniques to minimise the loss on sequentially generated weak learners to end up with an overall model

I highly recommend watching Josh Starmer's video on it for a detailed explanation as he does it better than I could ever.  [Link](https://www.youtube.com/watch?v=KXOTSkPL2X4)