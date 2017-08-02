# Day 2 - Wave

Today we'll train TJBot to wave using the wave node.

[![IMAGE ALT TEXT](http://img.youtube.com/vi/uE8pvLttipU/0.jpg)](http://www.youtube.com/watch?v=uE8pvLttipU "Train TJBot to Wave in Node-RED ")

## Flow

The flow consists of two nodes, an inject node to trigger the flow, and a wave node to command the TJBot to wave up and down.

![Wave Flow](assets/flow.png)

## Flow JSON
```
[{"id":"a93fc14b.116548","type":"inject","z":"4f8a700b.20a01","name":"Wave","topic":"","payload":"","payloadType":"date","repeat":"","crontab":"","once":false,"x":190,"y":200,"wires":[["b6c80e29.2ffca"]]},{"id":"b6c80e29.2ffca","type":"tjbot-wave","z":"4f8a700b.20a01","botId":"e12946d4.bddad","motion":"wave","name":"","x":340,"y":200,"wires":[]},{"id":"e12946d4.bddad","type":"tjbot-config","z":"","botGender":"male","name":"TJBot","hasLED":false,"hasServo":true}]
```

## Tips

* The inject node is useful when you want to manually trigger a flow
* Make sure to enable the servo in the TJBot configuration 

## Extra Credit

* Change the inject node to inject every five seconds
* Set the mode programmatically with `msg.mode` and the value `wave`

## Resources

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.