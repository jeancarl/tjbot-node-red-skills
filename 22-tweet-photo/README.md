# Day 22 - Take A Photo And Tweet It

Today we'll train TJBot to take a photo with the see node and the Raspberry Pi camera and post it to Twitter.

[![Train TJBot to Tweet a Photo in Node-RED](http://img.youtube.com/vi/Ejg7B4UvBjI/0.jpg)](https://www.youtube.com/watch?v=Ejg7B4UvBjI&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV&index=25 "Train TJBo to Tweet a Photo in Node-RED") 

## Flow

The flow consists of an inject node to inject a string, I'm hungry, a converse node to process the natural language with the Watson Conversation service, and a debug node to display the response from the Watson Conversation service.

![Take A Photo And Tweet It Flow](assets/flow.png) 

## Flow JSON

```
[{"id":"1061081a.f3068","type":"inject","z":"4f8a700b.20a01","name":"Take Photo","topic":"","payload":"","payloadType":"date","repeat":"","crontab":"","once":false,"x":160,"y":160,"wires":[["d7e41d8a.aa471"]]},{"id":"d7e41d8a.aa471","type":"tjbot-see","z":"4f8a700b.20a01","botId":"4275751d.01daf4","mode":"takephoto","verticalFlip":true,"horizontalFlip":true,"width":"640","height":"480","name":"","x":290,"y":160,"wires":[["f56631a9.e0c018"]]},{"id":"f56631a9.e0c018","type":"file in","z":"4f8a700b.20a01","name":"","filename":"","format":"","chunk":false,"sendError":false,"x":410,"y":160,"wires":[["31688c83.65a56c"]]},{"id":"31688c83.65a56c","type":"change","z":"4f8a700b.20a01","name":"","rules":[{"t":"set","p":"media","pt":"msg","to":"payload","tot":"msg"},{"t":"set","p":"payload","pt":"msg","to":"Hello from #TJBot","tot":"str"}],"action":"","property":"","from":"","to":"","reg":false,"x":560,"y":160,"wires":[["1bc9de9d.071101"]]},{"id":"1bc9de9d.071101","type":"twitter out","z":"4f8a700b.20a01","twitter":"","name":"Tweet","x":710,"y":160,"wires":[]},{"id":"4275751d.01daf4","type":"tjbot-config","z":"","botGender":"male","name":"TJBot","speak":"en-US","hasServo":false,"hasLED":false,"hasSpeaker":false,"hasMicrophone":false,"hasCamera":true,"speakerDeviceId":"plughw:0,0"}]

```

## Tips

* Don't forget to create a Watson Visual Recognition service and use the service credentials in the TJBot configuration

## Extra Credit

* Use a listen node to transcribe audio and use it as the text for the tweet
* Shine a light to signal that TJBot is taking the photo
* Use the speaker to play audio as TJBot takes the photo
	
## Resources

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.
