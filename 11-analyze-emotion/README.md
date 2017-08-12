# Day 11 - Analyze Emotion

Today we’ll train TJBot to analyze the emotions of an utterance and light the LED one of five colors representing the most prevalent emotion: anger, disgust, fear, joy, and sadness.

* Anger - red
* Disgust - green
* Fear - magenta
* Joy - yellow
* Sadness - blue

[![Train TJBot to Analyze Emotions in Node-RED](http://img.youtube.com/vi/ggED7bpr2dg/0.jpg)](https://www.youtube.com/watch?v=ggED7bpr2dg&index=13&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV "Train TJBot to Analyze Emotions in Node-RED") 

## Flow

The flow consists of two inject nodes to start and stop listening using the microphone, a listen node to listen and transcribe audio into English using the Watson Speech to Text service, an analyze tone node to analyze the emotions perceived in the utterance using the Watson Tone Analyzer service, a function node to find the top scoring emotion, and a switch node to branch into one of the five shine nodes to shine the color representing the top emotion.

![Analyze Emotions](assets/flow.png)

## Flow JSON
```
[{"id":"d051094f.86cd28","type":"inject","z":"4f8a700b.20a01","name":"Start Listening","topic":"","payload":"start","payloadType":"str","repeat":"","crontab":"","once":false,"x":110,"y":140,"wires":[["b9f74ec1.b41a7"]]},{"id":"4cafcf33.0e3a18","type":"inject","z":"4f8a700b.20a01","name":"Stop Listening","topic":"","payload":"stop","payloadType":"str","repeat":"","crontab":"","once":false,"x":110,"y":180,"wires":[["b9f74ec1.b41a7"]]},{"id":"b9f74ec1.b41a7","type":"change","z":"4f8a700b.20a01","name":"","rules":[{"t":"set","p":"mode","pt":"msg","to":"payload","tot":"msg"}],"action":"","property":"","from":"","to":"","reg":false,"x":280,"y":160,"wires":[["f2edee78.fe0a28"]]},{"id":"f2edee78.fe0a28","type":"tjbot-listen","z":"4f8a700b.20a01","botId":"f6934ab3.f20f2","name":"","x":430,"y":160,"wires":[["2fa3328f.2b474e"]]},{"id":"2fa3328f.2b474e","type":"tjbot-analyze-tone","z":"4f8a700b.20a01","botId":"f6934ab3.f20f2","tones":"emotion","name":"","x":570,"y":160,"wires":[["2d820667.8d1bfa","f16528f3.8a4f4"]]},{"id":"2d820667.8d1bfa","type":"function","z":"4f8a700b.20a01","name":"Find Top Emotion","func":"var emotions = msg.response.tones;\n\nmsg.payload = emotions[Object.keys(emotions)\n            .reduce(function(a, b){\n                return emotions[a].score > emotions[b].score ? a : b\n\n            })];\n            \nreturn msg;","outputs":1,"noerr":0,"x":770,"y":160,"wires":[["d8b15838.e5e0f"]]},{"id":"d8b15838.e5e0f","type":"switch","z":"4f8a700b.20a01","name":"","property":"payload.tone_id","propertyType":"msg","rules":[{"t":"eq","v":"anger","vt":"str"},{"t":"eq","v":"disgust","vt":"str"},{"t":"eq","v":"fear","vt":"str"},{"t":"eq","v":"joy","vt":"str"},{"t":"eq","v":"sadness","vt":"str"}],"checkall":"false","outputs":5,"x":930,"y":160,"wires":[["492ee066.934d78"],["9d10bbe7.416a5"],["d5cdf0a6.570128"],["4ffd2973.ebb958"],["7aeab2d8.9c96dc"]]},{"id":"492ee066.934d78","type":"tjbot-shine","z":"4f8a700b.20a01","botId":"f6934ab3.f20f2","mode":"shine","color":"red","duration":"","name":"","x":1080,"y":80,"wires":[]},{"id":"9d10bbe7.416a5","type":"tjbot-shine","z":"4f8a700b.20a01","botId":"f6934ab3.f20f2","mode":"shine","color":"green","duration":"","name":"","x":1090,"y":120,"wires":[]},{"id":"d5cdf0a6.570128","type":"tjbot-shine","z":"4f8a700b.20a01","botId":"f6934ab3.f20f2","mode":"shine","color":"magenta","duration":"","name":"","x":1100,"y":160,"wires":[]},{"id":"4ffd2973.ebb958","type":"tjbot-shine","z":"4f8a700b.20a01","botId":"f6934ab3.f20f2","mode":"shine","color":"yellow","duration":"","name":"","x":1090,"y":200,"wires":[]},{"id":"7aeab2d8.9c96dc","type":"tjbot-shine","z":"4f8a700b.20a01","botId":"f6934ab3.f20f2","mode":"shine","color":"blue","duration":"","name":"","x":1090,"y":240,"wires":[]},{"id":"f16528f3.8a4f4","type":"debug","z":"4f8a700b.20a01","name":"","active":true,"console":"false","complete":"true","x":730,"y":220,"wires":[]},{"id":"f6934ab3.f20f2","type":"tjbot-config","z":"","botGender":"male","name":"TJBot","listen":"en-US","hasLED":true,"hasServo":false,"speakerDeviceId":"plughw:0,0"}]
```

## Find Top Emotion JavaScript Function


```
var emotions = msg.response.tones;

msg.payload = emotions[Object.keys(emotions)
            .reduce(function(a, b){
                return emotions[a].score > emotions[b].score ? a : b

            })];

return msg;
```

## Tips

* Don't forget to create a Watson Speech to Text and Watson Tone Analyzer service and use the service credentials in the TJBot configuration

## Extra Credit

* Instead of shining a solid color, use the pulse mode 
	
## Resources

Read more about the scores and science behind the service in the [Watson Tone Analyzer documentation](https://www.ibm.com/watson/developercloud/doc/tone-analyzer/index.html).

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.
