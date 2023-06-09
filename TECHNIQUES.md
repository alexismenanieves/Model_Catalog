TECHNIQUES

Market Basket Analysis using PySpark
https://towardsdatascience.com/market-basket-analysis-using-pysparks-fpgrowth-55c37ebd95c0

Recommend using Scikit-Learn and Tensorflow Recommender
https://towardsdatascience.com/recommend-using-scikit-learn-and-tensorflow-recommender-bc659d91301a?gi=a0a230b283d8

CODING

https://stackoverflow.com/questions/44864633/pythonic-way-to-find-maximum-absolute-value-of-list
>>> abs(max([3, 7, -10], key=abs))

https://stackoverflow.com/questions/6910641/how-do-i-get-indices-of-n-maximum-values-in-a-numpy-array
>>> a = np.array([9, 4, 4, 3, 3, 9, 0, 4, 6, 0])
>>> ind = np.argpartition(a, -4)[-4:]
>>> ind
array([1, 5, 8, 0])
>>> top4 = a[ind]
>>> top4
array([4, 9, 6, 9])

ALGORITHMS

Implementation of the LOWESS algorithm in n dimensions
https://github.com/arokem/lowess/blob/master/lowess/lowess.py

Cook Distance
https://github.com/NicolasWoloszko/CookDistance/blob/master/cookdistance.py

