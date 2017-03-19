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
?
```

Run

```bash
python main.py
```

Output

```
?
```

References

* http://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html
* https://www.slideshare.net/SarahGuido/kmeans-clustering-with-scikitlearn
* http://scikit-learn.org/stable/auto_examples/cluster/plot_kmeans_silhouette_analysis.html
