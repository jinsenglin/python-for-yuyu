# Sample project 7

Open terminal and run

```bash
pyenv shell 2.7.13

cd ~/Desktop/venvs

virtualenv sample7

source ~/Desktop/venvs/sample7/bin/activate

git clone https://github.com/jwlin/ptt-web-crawler.git ~/Desktop/venvs/sample6/src
cd ~/Desktop/venvs/sample6/src

pip install -r requirements.txt
```

Run

```bash
python crawler.py -b PublicServan -i 100 200
```

Output

```
?
```

References

* https://github.com/jwlin/ptt-web-crawler
