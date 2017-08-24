# Day 23 - Read Direct Messages

In this video, we'll train TJBot to receive direct messages from Twitter and read them aloud using the speak node in Node-RED.

[![Train TJBot to Read Direct Messages in Node-RED](http://img.youtube.com/vi/5xsEWM7NRbY/0.jpg)](https://www.youtube.com/watch?v=5xsEWM7NRbY&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV&index=26 "Train TJBot to Read Direct Messages in Node-RED") 

## Flow

The flow consists of an Twitter input node to receive direct messages, a speak node to read the messages aloud using the Watson Text to Speech service, and a debug node to display the message in the debug window.

![Read Direct Messages Flow](assets/flow.png) 

## Flow JSON

```
[{"id":"e3aa5ec9.d5056","type":"twitter in","z":"4f8a700b.20a01","twitter":"","tags":"","user":"dm","name":"","topic":"tweets","inputs":0,"x":250,"y":120,"wires":[["e0c9fb60.8cfd9","25097fe1.433498"]]},{"id":"e0c9fb60.8cfd9","type":"tjbot-speak","z":"4f8a700b.20a01","botId":"b494dfd5.c382d","mode":"speak","payload":"","name":"","x":410,"y":120,"wires":[[]]},{"id":"25097fe1.433498","type":"debug","z":"4f8a700b.20a01","name":"","active":true,"console":"false","complete":"false","x":430,"y":160,"wires":[]},{"id":"b494dfd5.c382d","type":"tjbot-config","z":"","botGender":"male","name":"TJBot","speak":"en-US","hasServo":false,"hasLED":false,"hasSpeaker":true,"hasMicrophone":false,"hasCamera":false,"speakerDeviceId":"plughw:2,0"}]
```

## Tips

* Authenticate the Twitter input node with a Twitter account
* Don't forget to create a Watson Text to Speech service and use the service credentials in the TJBot configuration


## Extra Credit

* Analyze the emotions or tones using the analyze tone node.
* Connect a converse node and train a Watson Conversation service to respond to direct messages
	
## Resources

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.
