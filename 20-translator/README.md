# Day 20 - Translator

Today we'll train TJBot how to listen, translate, and speak using the listen, translate, and speak nodes and the Watson Speech to Text, Language Translator, and Text to Speech service.

[![Train TJBot to Be a Tranlator in Node-RED](http://img.youtube.com/vi/4RjcFw9imv4/0.jpg)](https://www.youtube.com/watch?v=4RjcFw9imv4&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV&index=23 "Train TJBo to Be a Tranlator in Node-RED") 

## Flow

The flow consists of an inject node to start and stop the microphone, a change node to set the mode of the listen node, a listen node to transcribe audio into text using the Watson Speech to Text service, a translate node to translate what is heard into French using the Watson Language Translator service, a change node to set the payload to the translation, and a speak node to speak the translation in French using the Watson Text to Speech service.

![Translator Flow](assets/flow.png) 

## Flow JSON

```
[{"id":"11901576.5e5d1b","type":"inject","z":"4f8a700b.20a01","name":"Start Listening","topic":"","payload":"start","payloadType":"str","repeat":"","crontab":"","once":false,"x":170,"y":300,"wires":[["d2062d4e.472e98"]]},{"id":"19b21703.c6ff11","type":"inject","z":"4f8a700b.20a01","name":"Stop Listening","topic":"","payload":"stop","payloadType":"str","repeat":"","crontab":"","once":false,"x":170,"y":340,"wires":[["d2062d4e.472e98"]]},{"id":"d2062d4e.472e98","type":"change","z":"4f8a700b.20a01","name":"","rules":[{"t":"set","p":"mode","pt":"msg","to":"payload","tot":"msg"}],"action":"","property":"","from":"","to":"","reg":false,"x":340,"y":320,"wires":[["2119975b.4f9b68"]]},{"id":"2119975b.4f9b68","type":"tjbot-listen","z":"4f8a700b.20a01","botId":"2b1f4e7c.491b22","name":"","x":490,"y":320,"wires":[["c2c64fe5.dbe2c"]]},{"id":"c2c64fe5.dbe2c","type":"change","z":"4f8a700b.20a01","name":"","rules":[{"t":"delete","p":"mode","pt":"msg"}],"action":"","property":"","from":"","to":"","reg":false,"x":650,"y":320,"wires":[["e969b8.1196ee48"]]},{"id":"e969b8.1196ee48","type":"tjbot-translate","z":"4f8a700b.20a01","botId":"2b1f4e7c.491b22","srcLang":"en","targetLang":"fr","mode":"translate","name":"","x":820,"y":320,"wires":[["ad932967.516208"]]},{"id":"ad932967.516208","type":"change","z":"4f8a700b.20a01","name":"","rules":[{"t":"set","p":"payload","pt":"msg","to":"response.translations[0].translation","tot":"msg"}],"action":"","property":"","from":"","to":"","reg":false,"x":980,"y":320,"wires":[["2215b2b.456684e"]]},{"id":"2215b2b.456684e","type":"tjbot-speak","z":"4f8a700b.20a01","botId":"2b1f4e7c.491b22","mode":"speak","payload":"","name":"","x":1130,"y":320,"wires":[[]]},{"id":"2b1f4e7c.491b22","type":"tjbot-config","z":"","botGender":"male","name":"TJBot","listen":"en-US","speak":"fr-FR","hasServo":false,"hasLED":false,"hasSpeaker":true,"hasMicrophone":true,"hasCamera":false,"speakerDeviceId":"plughw:2,0"}]

```

## Tips

* Don't forget to create a Watson Speech to Text service, Watson Language Translator service, and Watson Text to Speech service and use the service credentials in the TJBot configuration
* Enable the microphone and speaker in the TJBot configuration

## Extra Credit

* Add additional training phrases to expand the vocabulary TJBot can understand
	
## Resources

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.
