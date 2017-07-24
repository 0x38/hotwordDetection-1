# Hotword detection service

A hotword ("hey alexa") detection service [(using snowboy)](https://snowboy.kitt.ai/) for raspberry pi 

# Setup 


Install dependency

```
sudo apt-get install sox mplayer swig3.0 python-pyaudio python3-pyaudio
pip install pyaudio
```

[Configure audio at raspberry pi ](https://permissiontowrite.wordpress.com/raspberry-pi-audio-setup/)

Install hotwordDetection command and add to a well known folder (so we can run in any place)

```
sudo mkdir /opt/hotwordDetection
sudo git clone git@github.com:neyfrota/hotword-detection-service.git /opt/hotwordDetection
sudo ln -s /opt/hotwordDetection/hotwordDetection /usr/bin/hotwordDetection
``` 

Check command usage
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
hotwordDetection --action "echo 'My action'"
```
```
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

Play a beep each "hey alexa"
```
hotwordDetection --action 'play /opt/hotwordDetection/beep.wav'
``` 

[Ask alexa](https://github.com/neyfrota/alexa-command-line-client) each "hey alexa"
```
hotwordDetection --action 'alexa ask'
``` 


# Credits

* [snowboy](https://snowboy.kitt.ai/) framework to detect "ḧey alexa" hotword.