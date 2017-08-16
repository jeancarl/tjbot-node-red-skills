# Day 15 - Identify Colors

Today we’ll train TJBot to identify colors using the see node and the Watson Visual Recognition service.

[![Train TJBot to Identify Colors in Node-RED](http://img.youtube.com/vi/utIkn_Qkc_Y/0.jpg)](https://www.youtube.com/watch?v=utIkn_Qkc_Y&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV&index=18 "Train TJBot to Identify Colors in Node-RED") 

## Flow

The flow consists of an inject node to run the flow, a see node to recognize objects and colors using the Watson Visual Recognition service, a function node to format the list of colors from the results, and a debug node to output the result to the debug window.

![Identify Colors Flow](assets/flow.png) 

## Flow JSON

```
[{"id":"bc678cea.ae1d2","type":"inject","z":"4f8a700b.20a01","name":"Recognize Colors","topic":"","payload":"","payloadType":"date","repeat":"","crontab":"","once":false,"x":150,"y":220,"wires":[["cd1dbc10.66b59"]]},{"id":"345fd8ae.f3bc4","type":"function","z":"4f8a700b.20a01","name":"Find Colors","func":"msg.payload = msg.payload.filter(function(obj) {\n\treturn obj.class.match(/color$/);\n}).map(function(obj) {\n\treturn obj.class.replace(/ color$/, \"\");\n}).join(\", \");\n\nmsg.payload = msg.payload.length ? \"I see \"+msg.payload : \"I don't see any colors\";\n\nreturn msg;","outputs":1,"noerr":0,"x":450,"y":220,"wires":[["50ff7240.d653c4"]]},{"id":"50ff7240.d653c4","type":"debug","z":"4f8a700b.20a01","name":"","active":true,"console":"false","complete":"false","x":610,"y":220,"wires":[]},{"id":"cd1dbc10.66b59","type":"tjbot-see","z":"4f8a700b.20a01","botId":"ef9ae03a.92a7a","mode":"see","verticalFlip":false,"horizontalFlip":false,"width":960,"height":720,"name":"","x":310,"y":220,"wires":[["345fd8ae.f3bc4"]]},{"id":"ef9ae03a.92a7a","type":"tjbot-config","z":"","botGender":"male","name":"TJBot","hasServo":false,"hasLED":false,"hasSpeaker":false,"hasMicrophone":false,"hasCamera":true,"speakerDeviceId":"plughw:0,0"}]

```

## Find Colors JavaScript Function

```
msg.payload = msg.payload.filter(function(obj) {
	return obj.class.match(/color$/);
}).map(function(obj) {
	return obj.class.replace(/ color$/, "");
}).join(", ");

msg.payload = msg.payload.length ? "I see "+msg.payload : "I don't see any colors";

return msg;
```

## Tips

* Don't forget to create a Watson Visual Recognition service and use the service credentials in the TJBot configuration

## Extra Credit

* Filter low scoring colors out of the list
* Shine or pulse the LED the most prevalent color seen
	
## Resources

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.
