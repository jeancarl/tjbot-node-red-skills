# Day 26 - Measure CPU Temperature

Today we'll train TJBot to measure the CPU temperature and speak it out using the speaker and the Watson Text to Speech service.

[![Train TJBot to Measure CPU Temperature in Node-RED](http://img.youtube.com/vi/rXBh7zHM9b4/0.jpg)](https://www.youtube.com/watch?v=rXBh7zHM9b4&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV&index=29 "Train TJBot to Measure CPU Temperature in Node-RED") 

## Flow

The flow consists of an inject node to start the flow, a exec node to call a command to get the CPU temperature, a change node to clean up the response, a switch node to check if the temperature is above 44 degrees Celsius, two template nodes to construct the message, and a speak node to speak out the response using the Watson Text to Speech service via the speaker.

![Measure CPU Temperature Flow](assets/flow.png) 

## Flow JSON

```
[{"id":"cea34314.f766b8","type":"inject","z":"4f8a700b.20a01","name":"Measure CPU Temperature","topic":"","payload":"","payloadType":"date","repeat":"","crontab":"","once":false,"x":230,"y":320,"wires":[["e154fc36.d25d88"]]},{"id":"e154fc36.d25d88","type":"exec","z":"4f8a700b.20a01","command":"vcgencmd","addpay":true,"append":"measure_temp","useSpawn":"false","timer":"","oldrc":false,"name":"Get CPU Temperature","x":460,"y":320,"wires":[["d7fe8a29.0dcd08"],[],[]]},{"id":"d7fe8a29.0dcd08","type":"change","z":"4f8a700b.20a01","name":"","rules":[{"t":"change","p":"payload","pt":"msg","from":"[^0-9\\.]","fromt":"re","to":"","tot":"str"}],"action":"","property":"","from":"","to":"","reg":false,"x":680,"y":300,"wires":[["29109efc.eb4cca"]]},{"id":"29109efc.eb4cca","type":"switch","z":"4f8a700b.20a01","name":"Is It Warm In Here?","property":"payload","propertyType":"msg","rules":[{"t":"gt","v":"44.0","vt":"num"},{"t":"else"}],"checkall":"false","outputs":2,"x":890,"y":300,"wires":[["987a5ecb.e4a2b8"],["23e018da.96482"]]},{"id":"987a5ecb.e4a2b8","type":"template","z":"4f8a700b.20a01","name":"Warm","field":"payload","fieldType":"msg","format":"handlebars","syntax":"mustache","template":"Is it warm in here? My CPU temperature is {{payload}} degrees celsius.","output":"str","x":1070,"y":280,"wires":[["15287ca4.2075db"]]},{"id":"23e018da.96482","type":"template","z":"4f8a700b.20a01","name":"Normal","field":"payload","fieldType":"msg","format":"handlebars","syntax":"mustache","template":"My CPU temperature is {{payload}} degrees celsius.","output":"str","x":1080,"y":320,"wires":[["15287ca4.2075db"]]},{"id":"15287ca4.2075db","type":"tjbot-speak","z":"4f8a700b.20a01","botId":"83733594.60494","mode":"speak","payload":"","name":"","x":1230,"y":300,"wires":[[]]},{"id":"83733594.60494","type":"tjbot-config","z":"","botGender":"male","name":"TJBot","hasServo":false,"hasLED":false,"hasSpeaker":false,"hasMicrophone":false,"hasCamera":false,"speakerDeviceId":"plughw:0,0"}]
```

## Tips

* Don't forget to enable the hardware for the speaker and add Watson Text to Speech service credentials.

## Extra Credit

* Use an time interval to check the temperature regularly, but only have the TJBot speak when the temperature is reaching critical.
	
## Resources

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.
