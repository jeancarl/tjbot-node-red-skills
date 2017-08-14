# Day 14 - Spell Words

Today we’ll train TJBot to spell out the letters of words using the speak node and the Watson Text to Speech service.

[![Train TJBot to Spell Words in Node-RED](http://img.youtube.com/vi/lBi5O925PNs/0.jpg)](https://www.youtube.com/watch?v=lBi5O925PNs&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV&index=17 "Train TJBot to Spell Words in Node-RED") 

## Flow

The flow consists of an inject node with the words to spell out, a template node that wraps the contents with SSML to instruct the Watson Text to Speech service to pronounce the letters individually, and a speak node to play the synthesized audio via the speaker.

![Identify Language and Translate Flow](assets/flow.png) 

## Flow JSON

```
[{"id":"a0d28a16.34094","type":"inject","z":"4f8a700b.20a01","name":"","topic":"","payload":"Hello","payloadType":"str","repeat":"","crontab":"","once":false,"x":170,"y":100,"wires":[["2170d874.e03c3"]]},{"id":"2170d874.e03c3","type":"template","z":"4f8a700b.20a01","name":"Format with SSML","field":"payload","fieldType":"msg","format":"handlebars","syntax":"mustache","template":"{{payload}}\nis spelled\n<speak>\n    <say-as interpret-as=\"letters\">{{payload}}</say-as>\n</speak>","output":"str","x":360,"y":100,"wires":[["3199ae73.82092a"]]},{"id":"3199ae73.82092a","type":"tjbot-speak","z":"4f8a700b.20a01","botId":"1262a4dd.1a50b3","mode":"speak","payload":"","name":"","x":560,"y":100,"wires":[[]]},{"id":"1262a4dd.1a50b3","type":"tjbot-config","z":"","botGender":"male","name":"TJBot","speak":"en-US","hasServo":false,"hasLED":false,"hasSpeaker":true,"hasMicrophone":false,"hasCamera":false,"speakerDeviceId":"plughw:1,0"}]

```

## Template Node to Format with SSML

```
{{payload}}
is spelled
<speak>
    <say-as interpret-as="letters">{{payload}}</say-as>
</speak>
```

## Tips

* Don't forget to create a Watson Text to Speech service and use the service credentials in the TJBot configuration

## Extra Credit

* Use other SSML tags to add a variation to spelling words
	
## Resources

Refer to the [Text to Speech documentation](https://www.ibm.com/watson/developercloud/doc/text-to-speech/SSML.html#say-as_tag) for more on the SSML syntax.

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.
