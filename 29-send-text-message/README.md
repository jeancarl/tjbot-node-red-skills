# Day 29 - Send A Text Message

Today we'll train TJBot to listen to the microphone and then send a text message via the Twilio service.

[![Train TJBot to Send A Text Message in Node-RED](http://img.youtube.com/vi/WQ7LiHp9wKk/0.jpg)](https://www.youtube.com/watch?v=WQ7LiHp9wKk&index=32&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV "Train TJBot to Send A Text Message in Node-RED") 

## Flow

The flow consists of an inject node to start the flow, two change nodes to set the msg.mode, a listen node to capture audio and transcribe it using the Watson Speech to Text service, and a Twilio node to send the text message.

![Send A Text Message Flow](assets/flow.png) 

## Flow JSON

```
[{"id":"1f9aa709.f492b1","type":"inject","z":"4f8a700b.20a01","name":"Start Listening","topic":"","payload":"","payloadType":"date","repeat":"","crontab":"","once":false,"x":210,"y":180,"wires":[["d32ac791.0606e"]]},{"id":"d32ac791.0606e","type":"change","z":"4f8a700b.20a01","name":"Start Listening","rules":[{"t":"set","p":"mode","pt":"msg","to":"start","tot":"str"}],"action":"","property":"","from":"","to":"","reg":false,"x":380,"y":180,"wires":[["9eb55082.687fd"]]},{"id":"b76fcc58.ad2148","type":"change","z":"4f8a700b.20a01","name":"Stop Listening","rules":[{"t":"set","p":"mode","pt":"msg","to":"stop","tot":"str"}],"action":"","property":"","from":"","to":"","reg":false,"x":380,"y":240,"wires":[["9eb55082.687fd"]]},{"id":"9eb55082.687fd","type":"tjbot-listen","z":"4f8a700b.20a01","botId":"bc2676ce.fe6be","name":"","x":540,"y":220,"wires":[["418d4dcd.5e7624","b76fcc58.ad2148"]]},{"id":"418d4dcd.5e7624","type":"twilio out","z":"4f8a700b.20a01","service":"_ext_","twilio":"b6f5ae9a.d60a58","from":"","number":"+16502674832","name":"","x":700,"y":220,"wires":[]},{"id":"bc2676ce.fe6be","type":"tjbot-config","z":"","botGender":"male","name":"TJBot","listen":"en-US","hasServo":false,"hasLED":false,"hasSpeaker":false,"hasMicrophone":true,"hasCamera":false,"speakerDeviceId":"plughw:0,0"},{"id":"b6f5ae9a.d60a58","type":"twilio-api","z":"","sid":"ACe6fd4d535b81fb6652e4b8795bc038f1","from":"+13343104580","name":""}]
```

## Tips

* Don't forget to enable the hardware for the microphone and add the Watson Speech to Text service credentials

## Extra Credit

* Add a contacts list that can be used to send a message to different contacts
	
## Resources

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.
