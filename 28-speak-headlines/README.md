# Day 28 - Speak Headlines

Today we'll train TJBot to speak the headlines from an RSS feed using the Watson Text to Speech service and the speak node.

[![Train TJBot to Speak Headlines in Node-RED](http://img.youtube.com/vi/12_wa1pR_K8/0.jpg)](https://www.youtube.com/watch?v=12_wa1pR_K8&index=31&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV "Train TJBot to Speak Headlines in Node-RED") 

## Flow

The flow consists of a feedparse node that reads a RSS feed, a delay node to limit one headline per minute, and a speak node to speak the headline using the Watson Text to Speech service and the speaker.

![Speak Headlines Flow](assets/flow.png) 

## Flow JSON

```
[{"id":"f2e9af34.1d9fa","type":"feedparse","z":"4f8a700b.20a01","name":"","url":"https://www.nytimes.com/svc/collections/v1/publish/https://www.nytimes.com/section/aponline/news/rss.xml","interval":"5","x":460,"y":980,"wires":[["62627d04.535cdc"]]},{"id":"62627d04.535cdc","type":"delay","z":"4f8a700b.20a01","name":"","pauseType":"rate","timeout":"5","timeoutUnits":"seconds","rate":"1","nbRateUnits":"1","rateUnits":"minute","randomFirst":"1","randomLast":"5","randomUnits":"seconds","drop":true,"x":940,"y":980,"wires":[["7394e269.cd0dfc"]]},{"id":"7394e269.cd0dfc","type":"tjbot-speak","z":"4f8a700b.20a01","botId":"e12d4d03.5e455","mode":"speak","payload":"","name":"","x":1110,"y":980,"wires":[[]]},{"id":"e12d4d03.5e455","type":"tjbot-config","z":"","botGender":"male","name":"TJBot","hasServo":false,"hasLED":false,"hasSpeaker":true,"hasMicrophone":false,"hasCamera":false,"speakerDeviceId":"plughw:2,0"}]
```

## Tips

* Don't forget to enable the hardware for the speaker and add Watson Text to Speech service credentials

## Extra Credit

* Translate the headlines to another language and then speak it out
	
## Resources

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.
