# Day 24 - Play Sounds

In this video, we'll train TJBot to play sounds using the speak node in Node-RED.

[![Train TJBot to Read Direct Messages in Node-RED](http://img.youtube.com/vi/guoJlkHCHGk/0.jpg)](https://www.youtube.com/watch?v=guoJlkHCHGk&list=PLddOPkVMzPlay SoundsRead Direct Messages in Node-RED") 

## Flow

The flow consists of an inject node with a file path to an audio file and a speak node in play mode to play the audio file.

![Play Sounds Flow](assets/flow.png) 

## Flow JSON

```
[{"id":"20e4dbde.cce7fc","type":"inject","z":"4f8a700b.20a01","name":"Laugh","topic":"","payload":"/usr/share/scratch/Media/Sounds/Human/Laugh-female.wav","payloadType":"str","repeat":"","crontab":"","once":false,"x":150,"y":160,"wires":[["992482ba.2b7c1"]]},{"id":"992482ba.2b7c1","type":"tjbot-speak","z":"4f8a700b.20a01","botId":"605d8a15.b60dd4","mode":"play","payload":"","name":"","x":300,"y":160,"wires":[[]]},{"id":"4ceba47a.2990fc","type":"inject","z":"4f8a700b.20a01","name":"Cough","topic":"","payload":"/usr/share/scratch/Media/Sounds/Human/Cough-male.wav","payloadType":"str","repeat":"","crontab":"","once":false,"x":150,"y":200,"wires":[["992482ba.2b7c1"]]},{"id":"605d8a15.b60dd4","type":"tjbot-config","z":"","botGender":"male","name":"TJBot","speak":"en-US","hasServo":false,"hasLED":false,"hasSpeaker":true,"hasMicrophone":false,"hasCamera":false,"speakerDeviceId":"plughw:2,0"}]
```

## Tips

* Look through the Sounds folder for other sound effects to play.


## Extra Credit

* Use a change node to set the msg.payload if you place this in the middle of a flow.
	
## Resources

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.
