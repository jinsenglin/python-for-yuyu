# K-means

Open terminal and run

```bash
pyenv shell 2.7.13

cd ~/Desktop/venvs

virtualenv k-means

source ~/Desktop/venvs/k-means/bin/activate

pip install numpy scipy scikit-learn matplotlib

mkdir ~/Desktop/venvs/k-means/src
cd ~/Desktop/venvs/k-means/src

echo 'backend: TkAgg' > ~/.matplotlib/matplotlibrc
```

Create a file named main.py with following content:

```py
from sklearn.cluster import KMeans
import numpy as np

X = np.array([[1, 2], [1, 4], [1, 0],
              [4, 2], [4, 4], [4, 0]])

kmeans = KMeans(n_clusters=2, random_state=0).fit(X)
print(kmeans.labels_)

print(kmeans.predict([[0, 0], [4, 4]]))

print(kmeans.cluster_centers_)
```

Run

```bash
python main.py
```

Output

```
[0 0 0 1 1 1]
[0 1]
[[ 1.  2.]
 [ 4.  2.]]
```

References

* http://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html
* https://www.slideshare.net/SarahGuido/kmeans-clustering-with-scikitlearn
