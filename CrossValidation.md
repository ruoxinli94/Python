[Sklearn Documents](https://scikit-learn.org/stable/modules/cross_validation.html#cross-validation)

### K-Folds Cross Validation
usually K=5 or 10 
```python
Import numpy as np
from sklearn.model_selection import KFold
X = np.array([[1, 2], [3, 4], [1, 2], [3, 4], [1,4]]) # sample data for predictors
y = np.array([1, 2, 3, 4, 5]) # sample data for response
kf = KFold(n_splits=5) # Define the split - into 5 folds 
kf.get_n_splits(X) # returns the number of splitting iterations in the cross-validator
```
print result of the kfold
```python
for train_ind, test_ind in kf.split(X):
    print(x_train, x_test)
    x_train,x_test = X[train_ind],X[test_ind]
    y_train,y_test = y[train_ind],y[test_ind]
```

### Leave p out Cross Validation (p=1)
p=1 reduce the computation burden, the number of group is equal to the number of observations in the dataset. 
```python
from sklearn.model_selection import LeaveOneOut 
X = np.array([[1, 2], [3, 4]])
y = np.array([1, 2])
loo = LeaveOneOut()
loo.get_n_splits(X)

for train_index, test_index in loo.split(X):
   print("TRAIN:", train_index, "TEST:", test_index)
   X_train, X_test = X[train_index], X[test_index]
   y_train, y_test = y[train_index], y[test_index]
   print(X_train, X_test, y_train, y_test)
```

output like below:
```python
TRAIN: [1] TEST: [0]
[[3 4]] [[1 2]] [2] [1]
TRAIN: [0] TEST: [1]
[[1 2]] [[3 4]] [1] [2]
```

#### More instructions on [scikit learn web page](https://scikit-learn.org/stable/modules/cross_validation.html#cross-validation)

* methods based on KFold
  * [K-fold iterator variant with non-overlapping groups.](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GroupKFold.html#sklearn.model_selection.GroupKFold)
  * [Repeated K-Fold cross validator.](http://scikit-learn.org/stable/modules/generated/sklearn.model_selection.RepeatedKFold.html#sklearn.model_selection.RepeatedKFold)
  * [Repeated Stratified K-Fold cross validator.](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.RepeatedStratifiedKFold.html#sklearn.model_selection.RepeatedStratifiedKFold)
  * [Stratified K-Folds cross-validator](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.StratifiedKFold.html#sklearn.model_selection.StratifiedKFold)
```python
from sklearn import model_selection as ms
kf = ms.GroupKFold(n_splits = n)
kf = ms. RepeatedKFold(n_splits = n)
kf = ms.RepeatedStratifiedKFold()
kf = ms.StratifiedKFold()
```

* methods based on leave-one-out
 * [Leave One Group Out cross-validator](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.LeaveOneGroupOut.html#sklearn.model_selection.LeaveOneGroupOut)
 * [Leave P Group(s) Out cross-validator](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.LeavePGroupsOut.html#sklearn.model_selection.LeavePGroupsOut)
 * [Leave-One-Out cross-validator](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.LeaveOneOut.html#sklearn.model_selection.LeaveOneOut)
 * [Leave-P-Out cross-validator](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.LeavePOut.html#sklearn.model_selection.LeavePOut)
```python
logo = ms.LeaveOneGroupOut()
lpgo = ms.LeavePGroupOut(n_groups = n)
loo = ms.LeaveOneOut()
lgo = ms.LeavePOut(p)
```

* other methods 
 * [Shuffle-Group(s)-Out cross-validation iterator](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GroupShuffleSplit.html#sklearn.model_selection.GroupShuffleSplit)
 * [Predefined split cross-validator](http://scikit-learn.org/stable/modules/generated/sklearn.model_selection.PredefinedSplit.html#sklearn.model_selection.PredefinedSplit)
 * [Random permutation cross-validator](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.ShuffleSplit.html#sklearn.model_selection.ShuffleSplit)
 * [Time Series cross-validator](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.TimeSeriesSplit.html#sklearn.model_selection.TimeSeriesSplit)
