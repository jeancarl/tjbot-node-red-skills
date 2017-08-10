# Day 10 - Converse

Today we’ll train TJBot to respond using the converse node and the Watson Conversation service.

[![Train TJBot to Converse in Node-RED](http://img.youtube.com/vi/IxQN3CLVt88/0.jpg)](https://www.youtube.com/watch?v=IxQN3CLVt88&index=13&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV "Train TJBot to Converse in Node-RED") 

## Flow

The flow consists of an inject node to inject a blank payload string, a converse node to process the content via Watson Conversation, and a debug node to output the response to the debug window.

![Converse Flow](assets/flow.png)

## Flow JSON
```
[{"id":"4c35a572.d29c24","type":"inject","z":"4f8a700b.20a01","name":"Start Conversation","topic":"","payload":"","payloadType":"date","repeat":"","crontab":"","once":false,"x":290,"y":280,"wires":[["13d6e0e1.f1b937"]]},{"id":"13d6e0e1.f1b937","type":"tjbot-converse","z":"4f8a700b.20a01","botId":"aab590a5.5053b8","name":"","x":480,"y":280,"wires":[["373f883a.a317e8"]]},{"id":"373f883a.a317e8","type":"debug","z":"4f8a700b.20a01","name":"","active":true,"console":"false","complete":"response","x":670,"y":280,"wires":[]},{"id":"aab590a5.5053b8","type":"tjbot-config","z":"","botGender":"male","name":"TJBot","hasLED":false,"hasServo":false,"speakerDeviceId":"plughw:0,0"}]
```

## Tips

* Don't forget to create a Watson Conversation service and use the service credentials in the TJBot configuration

## Extra Credit

* Dive into the `msg.response.output` property and display just the text returned from the Conversation API in the debug window
	
## Resources

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.
