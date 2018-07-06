### Scikit-Learn Chapter 1

```
import numpy as np
x = np.array([[1, 2, 3], [4, 5, 6]])
x
```

```
from scipy import sparse
eye = np.eye(4)
print("Numpy array:\n%", % eye)
```

```
import matplotlib.pyplot as plt
x = np.arange(20)
y = np.sin(x)
plt.plot(x, y, marker="x")
plt.show()
```

```
import pandas as pd
data = {'Name': ["Johne", "Anna", "Peter", "Linda"],
            'Location': ["New York", "Paris", "Berlin", "London"],
            'Age': [24, 13, 53, 33]}
data_pandas = pd.DataFrame(data)
data_pandas
```

```
import pandas as pd
print("pandas version: %s" % pd.__version__)

import matplotlib
print("matplotlib version: %s" % matplotlib.__version__)

import numpy as np
print("numpy version: %s" % np.__version__)

import sklearn
print("scikit-learn version: %s" % sklearn.__version__)
```

```
from sklearn.datasets import load_iris
iris = load_iris()
iris.keys()
print(iris['DESCR'][:193] + "\n...")
iris['target_names']
iris['feature_names']
type(iris['data'])
iris['data'].shape
iris['data'][:5]
type(iris['target'])
iris['target'].shape
iris['target']

from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(iris['data'], iris['target'],
                                                        random_state=0)
X_train.shape
X_test.shape

for i in range(3):
        for j in range(3):
            ax[i, j].scatter(X_train[:, j], X_train[:, i + 1], c=y_train, s=60)
            ax[i, j].set_xticks(())
            ax[i, j].set_yticks(())
            if i == 2:
                ax[i, j].set_xlabel(iris['feature_names'][j])
            if j == 0:
                ax[i, j].set_ylabel(iris['feature_names'][i + 1])
            if j > i:
                ax[i, j].set_visible(False)
                
from sklearn.neighbors import KNeighborsClassifier
knn = KNeighborsClassifier(n_neighbors=1)
knn.fit(X_train, y_train)

y_pred = knn.predict(X_test)
np.mean(y_pred == y_test)


knn.score(X_test, y_test)
```
