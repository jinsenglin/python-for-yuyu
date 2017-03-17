# Sample project 1

Open terminal and run

```bash
pyenv shell 2.7.13

cd ~/Desktop/venvs

virtualenv sample1

source ~/Desktop/venvs/sample1/bin/activate

brew install portaudio
pip install pyaudio SpeechRecognition

mkdir ~/Desktop/venvs/sample1/src
cd ~/Desktop/venvs/sample1/src
```

Create a file named main.py with following content:

```py
import speech_recognition
r = speech_recognition.Recognizer()

with speech_recognition.Microphone() as source:
    audio = r.listen(source)

r.recognize_google(audio, language='zh-TW')
```

Run

```bash
python main.py
```

References

* http://www.largitdata.com/course/87/
