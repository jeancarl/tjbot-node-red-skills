# Day 12 - Identify Language

Today we’ll train TJBot to identify what language a phrase is using the Watson Language Translator Service.

[![Train TJBot to Identify Language in Node-RED](http://img.youtube.com/vi/RNiLn9WV3a0/0.jpg)](https://www.youtube.com/watch?v=RNiLn9WV3a0&index=15&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV "Train TJBot to Identify Language in Node-RED") 

## Flow

The flow consists of an inject node with a greeting, a translate node with the mode Identify Language, and a debug node to display the results from the Watson Language Translator service.

![Identify Language Flow](assets/flow.png)

## Flow JSON
```
[{"id":"29accbf5.49810c","type":"tjbot-translate","z":"245ca443.8b339c","botId":"f25fd4ef.dc8ff","srcLang":"","targetLang":"","mode":"identifyLanguage","name":"","x":360,"y":220,"wires":[["f1cd28b.0b2b758"]]},{"id":"31410468.bff1bc","type":"inject","z":"245ca443.8b339c","name":"","topic":"","payload":"Ciao","payloadType":"str","repeat":"","crontab":"","once":false,"x":210,"y":220,"wires":[["29accbf5.49810c"]]},{"id":"f1cd28b.0b2b758","type":"debug","z":"245ca443.8b339c","name":"","active":true,"console":"false","complete":"true","x":510,"y":220,"wires":[]},{"id":"f25fd4ef.dc8ff","type":"tjbot-config","z":"","botGender":"male","name":"TJBot"}]
```

## Tips

* Don't forget to create a Watson Language Translator service and use the service credentials in the TJBot configuration

## Extra Credit

* Write a JavaScript function to extract out the two letter language code for the highest scoring language identified
	
## Resources

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.
