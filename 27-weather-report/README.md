# Day 27 - Say Weather Report

Today we'll train TJBot to say the weather report using the Weather Insights node and the speak node.

[![Train TJBot to Say The Weather Report in Node-RED](http://img.youtube.com/vi/vDflosjm75I/0.jpg)](https://www.youtube.com/watch?v=vDflosjm75I&index=30&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV "Train TJBot to Say Weather Report in Node-RED") 

## Flow

The flow consists of an inject node to inject the geo-location, a Weather Insights node to get the current observation for the given location, a template node to construct a message with the current condition and temperature, and a speak node to speak the message using the Watson Text to Speech service and the speaker.

![Say Weather Report Flow](assets/flow.png) 

## Flow JSON

```
[{"id":"a0dc2816.3e3f8","type":"weather_insights","z":"4f8a700b.20a01","name":"","host":"twcservice.mybluemix.net","service":"/observations.json","geocode":"37.788485,-122.4066051","units":"e","language":"","x":320,"y":320,"wires":[["bfab5f4a.266ab"]]},{"id":"8cfecfb6.ed7e48","type":"inject","z":"4f8a700b.20a01","name":"San Francisco","topic":"","payload":"37.788485,-122.4066051","payloadType":"str","repeat":"","crontab":"","once":false,"x":150,"y":320,"wires":[["a0dc2816.3e3f8"]]},{"id":"bfab5f4a.266ab","type":"template","z":"4f8a700b.20a01","name":"Generate Message","field":"payload","fieldType":"msg","format":"handlebars","syntax":"mustache","template":"Currently {{observation.wx_phrase}} {{observation.temp}} degrees Farenheit.","output":"str","x":510,"y":320,"wires":[["4f2f553.121f4ac"]]},{"id":"4f2f553.121f4ac","type":"tjbot-speak","z":"4f8a700b.20a01","botId":"d7c368ef.80c2d","mode":"speak","payload":"","name":"","x":670,"y":320,"wires":[[]]},{"id":"d7c368ef.80c2d","type":"tjbot-config","z":"","botGender":"male","name":"TJBot","speak":"en-US","hasServo":false,"hasLED":false,"hasSpeaker":true,"hasMicrophone":false,"hasCamera":false,"speakerDeviceId":"plughw:2,0"}]
```

## Tips

* Don't forget to enable the hardware for the speaker and add Watson Text to Speech service credentials

## Extra Credit

* Use the forecast option and provide the user the forecast each morning
	
## Resources

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.
