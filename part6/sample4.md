# Sample project 4

Open terminal and run

```bash
pyenv shell 2.7.13

source ~/Desktop/venvs/sample3/bin/activate

cd ~/Desktop/venvs/sample3/src
```

Create a file named sample4.py with following content:

```py
from numpy import *

a = array([[2, -4, 4], [34, 3, -1], [1, 1, 1]])
b = array([8, 30, 108])
x = linalg.solve(a, b)
print(x)

a = array([[1, 1], [1, -1]])
b = [2, 0]
x = linalg.solve(a, b)
print(x)
```

Run by

```bash
python sample4.py
```

Output

```
[ -2.17647059  53.54411765  56.63235294]
[ 1.  1.]
```

References

* http://stackoverflow.com/questions/36354807/solving-linear-equations-w-three-variables-using-numpy
