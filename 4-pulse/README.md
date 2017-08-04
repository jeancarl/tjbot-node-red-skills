# Day 4 - Pulse

Today we'll train TJBot to pulse the LED red using the shine node and the mode pulse.

[![IMAGE ALT TEXT](http://img.youtube.com/vi/AkOWGQjlaXk/0.jpg)](http://www.youtube.com/watch?v=AkOWGQjlaXk "Train TJBot to Pulse LED in Node-RED")

## Flow

The flow consists of two nodes, an inject node to trigger the flow, and a shine node to command the TJBot to pulse the LED red for one second.

![Pulse Flow](assets/flow.png)

## Flow JSON
```
[{"id":"a93fc14b.116548","type":"inject","z":"4f8a700b.20a01","name":"Pulse Red","topic":"","payload":"","payloadType":"date","repeat":"","crontab":"","once":false,"x":200,"y":200,"wires":[["d8a6a830.6e5278"]]},{"id":"d8a6a830.6e5278","type":"tjbot-shine","z":"4f8a700b.20a01","botId":"e12946d4.bddad","mode":"pulse","color":"red","duration":"1","name":"","x":352.5,"y":200,"wires":[]},{"id":"e12946d4.bddad","type":"tjbot-config","z":"","botGender":"male","name":"TJBot","hasLED":true,"hasServo":false}]
```

## Tips

* The inject node is useful when you want to manually trigger a flow.
* Make sure to enable the LED in the TJBot configuration 

## Extra Credit

* Set the mode programmatically with `msg.mode` and the value `pulse`
* Set the duration programmatically with `msg.duration` and the value `1`
* Set the color programmatically with `msg.color` and the value `red`

## Resources

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.