# Sample project 7

Open terminal and run

```bash
pyenv shell 2.7.13

cd ~/Desktop/venvs

virtualenv sample7

source ~/Desktop/venvs/sample7/bin/activate

git clone https://github.com/jwlin/ptt-web-crawler.git ~/Desktop/venvs/sample7/src
cd ~/Desktop/venvs/sample7/src

pip install -r requirements.txt
```

Run

```bash
python crawler.py -b PublicServan -i 100 102
```

Output

```
Processing index: 100
/Users/cclin/Desktop/venvs/sample7/lib/python2.7/site-packages/bs4/__init__.py:181: UserWarning: No parser was explicitly specified, so I'm using the best available HTML parser for this system ("html.parser"). This usually isn't a problem, but if you run this code on another system, or in a different virtual environment, it may use a different parser and behave differently.

The code that caused this warning is on line 190 of the file crawler.py. To get rid of this warning, change code that looks like this:

 BeautifulSoup([your markup])

to this:

 BeautifulSoup([your markup], "html.parser")

  markup_type=markup_type))
Processing article: M.1257303884.A.A23
Processing article: M.1257309368.A.B43
Processing article: M.1257309908.A.DAB
Processing article: M.1257310931.A.B0B
Processing article: M.1257315001.A.957
Processing article: M.1257319654.A.C5B
Processing article: M.1257323934.A.4E8
Processing article: M.1257324168.A.1EF
Processing article: M.1257331573.A.CED
Processing article: M.1257336010.A.C4C
Processing article: M.1257336779.A.86A
Processing article: M.1257336817.A.5DC
Processing article: M.1257339619.A.F6E
Processing article: M.1257340509.A.ED9
Processing article: M.1257341433.A.70C
Processing article: M.1257342704.A.0BA
Processing article: M.1257343643.A.053
Processing article: M.1257344226.A.EDA
Processing article: M.1257344574.A.9B1
Processing article: M.1257345511.A.C1A
Processing index: 101
Processing article: M.1257345533.A.1EB
Processing article: M.1257348355.A.943
Processing article: M.1257349085.A.326
Processing article: M.1257349614.A.9E2
Processing article: M.1257349638.A.97A
Processing article: M.1257352785.A.B48
Processing article: M.1257378976.A.6D3
Processing article: M.1257382277.A.A79
Processing article: M.1257383768.A.742
Processing article: M.1257392093.A.D73
Processing article: M.1257402960.A.0F0
Processing article: M.1257405356.A.EF3
Processing article: M.1257408172.A.688
Processing article: M.1257409814.A.9D4
Processing article: M.1257412123.A.F8B
Processing article: M.1257414630.A.75A
Processing article: M.1257417593.A.DED
Processing article: M.1257420638.A.8B9
Processing article: M.1257421794.A.831
Processing article: M.1257439184.A.251
Processing index: 102
Processing article: M.1257442107.A.628
Processing article: M.1257462635.A.7C3
Processing article: M.1257467501.A.579
Processing article: M.1257475030.A.F30
Processing article: M.1257482734.A.DED
Processing article: M.1257488624.A.3F1
Processing article: M.1257489979.A.ED0
Processing article: M.1257496327.A.A17
Processing article: M.1257504074.A.033
Processing article: M.1257505079.A.21B
Processing article: M.1257505090.A.DEF
Processing article: M.1257513891.A.67A
Processing article: M.1257518691.A.DBB
Processing article: M.1257524305.A.04D
Processing article: M.1257525755.A.5C6
Processing article: M.1257527399.A.4A3
Processing article: M.1257552626.A.DC6
Processing article: M.1257564174.A.9F5
Processing article: M.1257566134.A.A29
Processing article: M.1257587893.A.F49
```

References

* https://github.com/jwlin/ptt-web-crawler
