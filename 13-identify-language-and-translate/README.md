# Day 13 - Identify Language and Translate

Today we’ll train TJBot to identify what language a greeting is in, check if there is a translation model to English, and translate it to English using the translate node and the Watson Language Translator service.

[![Train TJBot to Identify Language and Translate in Node-RED](http://img.youtube.com/vi/LPpXVrFXbAY/0.jpg)](https://www.youtube.com/watch?v=LPpXVrFXbAY&t=1s&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV&index=16 "Train TJBot to Identify Language and Translate in Node-RED") 

## Flow

The flow consists of two inject nodes with greetings in Italian and French, a translate node to identify the language of the greeting, a function node to find the language with the highest confidence score, another translate node to check that there is a translation model from the identified language to English, a switch node to check the value returned, a translation node to translate the greeting from identified language to English using the Watson Language Translator service, and a debug node to display the translation in the debug window.

![Identify Language and Translate Flow](assets/flow.png)

## Flow JSON

```
[{"id":"be4ecea.c9573b","type":"inject","z":"4f8a700b.20a01","name":"","topic":"","payload":"Ciao","payloadType":"str","repeat":"","crontab":"","once":false,"x":90,"y":80,"wires":[["1f32a2b8.24173d"]]},{"id":"1f32a2b8.24173d","type":"tjbot-translate","z":"4f8a700b.20a01","botId":"10ade00e.ced4c8","srcLang":"","targetLang":"","mode":"identifyLanguage","name":"Identify Language","x":250,"y":80,"wires":[["a941051d.52b238"]]},{"id":"a941051d.52b238","type":"function","z":"4f8a700b.20a01","name":"Detect Language","func":"var lang = msg.response.languages.reduce(function(a, b) {\n\treturn a.confidence > b.confidence ? a : b;\n});\n\nmsg.srcLang = lang.language;\n\nreturn msg;","outputs":1,"noerr":0,"x":450,"y":80,"wires":[["5b20b529.97ba5c"]]},{"id":"5b20b529.97ba5c","type":"tjbot-translate","z":"4f8a700b.20a01","botId":"10ade00e.ced4c8","srcLang":"msg.srcLang","targetLang":"en","mode":"isTranslatable","name":"Can translate to English?","x":670,"y":80,"wires":[["d99e0826.fc64f8"]]},{"id":"d99e0826.fc64f8","type":"switch","z":"4f8a700b.20a01","name":"","property":"response","propertyType":"msg","rules":[{"t":"true"}],"checkall":"true","outputs":1,"x":850,"y":80,"wires":[["424051b0.d96c98"]]},{"id":"424051b0.d96c98","type":"tjbot-translate","z":"4f8a700b.20a01","botId":"10ade00e.ced4c8","srcLang":"msg.srcLang","targetLang":"en","mode":"translate","name":"","x":1000,"y":80,"wires":[["3630344f.4f56d4"]]},{"id":"3630344f.4f56d4","type":"debug","z":"4f8a700b.20a01","name":"","active":true,"console":"false","complete":"response.translations[0].translation","x":1240,"y":80,"wires":[]},{"id":"dd17149c.11244","type":"inject","z":"4f8a700b.20a01","name":"","topic":"","payload":"Bonjour","payloadType":"str","repeat":"","crontab":"","once":false,"x":90,"y":120,"wires":[["1f32a2b8.24173d"]]},{"id":"10ade00e.ced4c8","type":"tjbot-config","z":"","botGender":"male","name":"TJBot","hasLED":false,"hasServo":false,"speakerDeviceId":"plughw:0,0"}]

```

## Detect Language JavaScript Function

```
var lang = msg.response.languages.reduce(function(a, b) {
	return a.confidence > b.confidence ? a : b;
});

msg.srcLang = lang.language;

return msg;
```

## Tips

* Don't forget to create a Watson Language Translator service and use the service credentials in the TJBot configuration

## Extra Credit

* Add an otherwise case to the switch node to handle the case when there is no translation model available
	
## Resources

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.
