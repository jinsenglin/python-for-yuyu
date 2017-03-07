# Install pyenv

Open terminal and run

```bash
brew update
brew install pyenv
```

Add `eval "$(pyenv init -)"` to your ~/.bash_profile by running

```bash
echo 'eval "$(pyenv init -)"' >> ~/.bash_profile
```

Run

```bash
source ~/.bash_profile
pyenv --version
```

Output
```
pyenv 1.0.8
```
