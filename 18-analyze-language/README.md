# Day 18 - Analyze Language Tones

Today we’ll train TJBot how to analyze language tones using the analyze tone node and the Watson Tone Analyzer service.

[![Train TJBot to Analyze Language Tones in Node-RED](http://img.youtube.com/vi/YNfDAbj_Ubk/0.jpg)](https://www.youtube.com/watch?v=YNfDAbj_Ubk&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV&index=21 "Train TJBot to Analyze Language Tones in Node-RED") 

## Flow

The flow consists of an inject node to run the flow, an analyze tone node to get the language tones using the Watson Tone Analyzer service, and a debug node to output the results to the debug window.

![Analyze Language Tones Flow](assets/flow.png) 

## Flow JSON

```
[{"id":"fcdecf44.73bbc8","type":"inject","z":"4f8a700b.20a01","name":"","topic":"","payload":"We will have to expand when we hire more people.","payloadType":"str","repeat":"","crontab":"","once":false,"x":130,"y":160,"wires":[["e03b3128.13819"]]},{"id":"e03b3128.13819","type":"tjbot-analyze-tone","z":"4f8a700b.20a01","botId":"5d3ae21f.53a23c","tones":"language","name":"","x":280,"y":160,"wires":[["68bff8f7.f0a13"]]},{"id":"68bff8f7.f0a13","type":"debug","z":"4f8a700b.20a01","name":"","active":true,"console":"false","complete":"response","x":470,"y":160,"wires":[]},{"id":"bbaa9de0.0e07c","type":"inject","z":"4f8a700b.20a01","name":"","topic":"","payload":"We might need to expand if we hire more people.","payloadType":"str","repeat":"","crontab":"","once":false,"x":130,"y":200,"wires":[["e03b3128.13819"]]},{"id":"5d3ae21f.53a23c","type":"tjbot-config","z":"","botGender":"male","name":"TJBot","hasServo":false,"hasLED":false,"hasSpeaker":false,"hasMicrophone":false,"hasCamera":false,"speakerDeviceId":"plughw:0,0"}]
```

## Tips

* Don't forget to create a Watson Tone Analyzer service and use the service credentials in the TJBot configuration

## Extra Credit

* Connect a listen node to analyze language tones in speech input
* Connect a function and speak node to output a human-friendly result.
	
## Resources

Refer to the [Watson Tone Analyzer documentation](https://console.bluemix.net/docs/services/tone-analyzer/using-tone.html#tones) to understand what the three language tones represent.

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.
