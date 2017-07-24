# Hotword detection service

A hotword ("hey alexa") detection service [(using snowboy)](https://snowboy.kitt.ai/) for my [Voice assistant](https://github.com/neyfrota/Billy-bass-voice-assistant/).

# Setup 

This doc is fine-tunned for my [raspberry pi setup](https://permissiontowrite.wordpress.com/2017/06/21/), but maybe work in other debians. 

### 1 - Install dependency


```
sudo apt-get install sox mplayer swig3.0 python-pyaudio python3-pyaudio
pip install pyaudio
```

### 2 - Install hotwordDetection

Install hotwordDetection (this repository) and add command to a well known folder so we can run in any place

```
sudo mkdir /opt/hotwordDetection
sudo git clone git@github.com:neyfrota/hotword-detection-service.git /opt/hotwordDetection
sudo ln -s /opt/hotwordDetection/hotwordDetection /usr/bin/hotwordDetection
``` 

### 3 - configure audio

Visit [raspberry pi audio setup](https://permissiontowrite.wordpress.com/2017/07/16/raspberry-pi-audio-setup/).

### 4 - check

Check command usage:
```
$ hotwordDetection 
usage: hotwordDetection [-h] [--model MODEL] [--action ACTION]

Use snowboy to detect a hotword (hey alexa) and trigger a command

optional arguments:
  -h, --help       show this help message and exit
  --model MODEL    snowboy .umdl model (default alexa.umdl)
  --action ACTION  Action to execute (required)

```

# Run
```
$ hotwordDetection --action "echo 'My action'"
Start hotword detection
model:  /opt/hotwordDetection/alexa.umdl
action: echo 'My action'
Listening... Press Ctrl+C to exit
```
At this point, hotwordDetection is listen microphone waiting for the hotword.
Try say "hey alexa". If all goes fine, we see a output like that:
```
Hotword detected
My action
Listening... Press Ctrl+C to exit
```
Hit control+c to stop 

# Examples

Now we can start real action like this:

* ```hotwordDetection --action 'play /opt/hotwordDetection/beep.wav'``` Play a beep each "hey alexa"
* ```hotwordDetection --action 'alexa ask'``` [Ask alexa](https://github.com/neyfrota/alexa-command-line-client) each "hey alexa"

# Credits
I cannot build this without help. **__"I am what I am because of who we all are"__**

* [snowboy](https://snowboy.kitt.ai/) framework to detect "ḧey alexa" hotword.