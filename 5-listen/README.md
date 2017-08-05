# Day 4 - Listen

Today we’ll train TJBot to listen using the microphone and the Watson Speech to Text service.

[![Train TJBot to Listen in Node-RED](http://img.youtube.com/vi/AFNUa7y5XeU/0.jpg)](https://www.youtube.com/watch?v=AFNUa7y5XeU&index=8&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV "Train TJBot to Listen in Node-RED")

## Flow

The flow consists of two inject nodes to start and stop listening, a change node to set the mode, a listen node to capture audio and transcribe into text, and a debug node to display the utterances in the debug window.

![Listen Flow](assets/flow.png)

## Flow JSON
```
[{"id":"9acdae42.396e88","type":"inject","z":"4f8a700b.20a01","name":"Start Listening","topic":"","payload":"start","payloadType":"str","repeat":"","crontab":"","once":false,"x":210,"y":320,"wires":[["67caa8b2.48d408"]]},{"id":"b5b224ef.c6a808","type":"inject","z":"4f8a700b.20a01","name":"Stop Listening","topic":"","payload":"stop","payloadType":"str","repeat":"","crontab":"","once":false,"x":210,"y":360,"wires":[["67caa8b2.48d408"]]},{"id":"67caa8b2.48d408","type":"change","z":"4f8a700b.20a01","name":"","rules":[{"t":"set","p":"mode","pt":"msg","to":"payload","tot":"msg"}],"action":"","property":"","from":"","to":"","reg":false,"x":400,"y":340,"wires":[["d1d38745.bc23e"]]},{"id":"d1d38745.bc23e","type":"tjbot-listen","z":"4f8a700b.20a01","botId":"e12946d4.bddad","name":"","x":570,"y":340,"wires":[["e45cafc1.12a33"]]},{"id":"e45cafc1.12a33","type":"debug","z":"4f8a700b.20a01","name":"","active":true,"console":"false","complete":"false","x":730,"y":340,"wires":[]},{"id":"e12946d4.bddad","type":"tjbot-config","z":"","botGender":"male","name":"TJBot","listen":"en-US","hasLED":false,"hasServo":false}]
```

## Tips

* The change node sets the `msg.mode` using the payload value from the inject node.

## Extra Credit

* Choose another language for TJBot to listen and transcribe into text
* Stop listening after a specified duration of time
* Stop listening after the first utterance is spoken

## Resources

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.