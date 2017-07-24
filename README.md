# Hotword detection service

A hotword ("hey alexa") detection tool [(using snowboy)](https://snowboy.kitt.ai/) for raspberry pi 

# Install


Install dependency

```
sudo apt-get install sox mplayer swig3.0 python-pyaudio python3-pyaudio
pip install pyaudio
```

[Configure raspberry pi audio](https://permissiontowrite.wordpress.com/raspberry-pi-audio-setup/)

Install and link to a well known folder (so we can run in any place) 
```
sudo git -C /opt/ clone https://github.com/neyfrota/hotwordDetection.git 
sudo ln -s /opt/hotwordDetection/hotwordDetection /usr/bin/hotwordDetection
``` 

# Run

Print "My action" each time you say "hey alexa"
```
hotwordDetection --action "echo 'My action'"
```
Check if listen

> ```
> Start hotword detection
> model:  /opt/hotwordDetection/alexa.umdl
> action: echo 'My action'
> Listening... Press Ctrl+C to exit
> ```

At this point, try to say "hey alexa". If all goes fine, we see a output like that:

> ```
> Hotword detected
> My action
> Listening... Press Ctrl+C to exit
> ```

Hit control+c to stop and try better examples.

Play a beep each "hey alexa"
```
hotwordDetection --action 'play /opt/hotwordDetection/beep.wav'
``` 

[Ask alexa](https://github.com/neyfrota/alexa-command-line-client) each "hey alexa"
```
hotwordDetection --action 'alexa ask'
``` 


# Credits

* [snowboy](https://snowboy.kitt.ai/) framework