# Sample project 3

Open terminal and run

```bash
pyenv shell 2.7.13

cd ~/Desktop/venvs

virtualenv sample3

source ~/Desktop/venvs/sample3/bin/activate

pip install numpy

mkdir ~/Desktop/venvs/sample3/src
cd ~/Desktop/venvs/sample3/src
```

Create a file named main.py with following content:

```py
from numpy import *

m1 = array([[1,3],[1,0],[1,2]])
m2 = array([[0,0],[7,5],[2,1]])
m3 = add(m1,m2)
print(m3)

m4 = matrix('1 3; 1 0; 1 2')
m5 = matrix('0 0; 7 5; 2 1')
m6 = add(m4,m5)
print(m6)
```

Run

```bash
python main.py
```

Output

```
[[1 3]
 [8 5]
 [3 3]]
[[1 3]
 [8 5]
 [3 3]]
```

References

* https://en.wikipedia.org/wiki/Matrix_addition
