# Day 21 - Suggest A Lunch Spot

Today we'll train TJBot to suggest a lunch spot using the converse node and the Watson Conversation service.

[![Train TJBot to Suggest A Lunch Spot in Node-RED](http://img.youtube.com/vi/Eaz_o7cnlaM/0.jpg)](https://www.youtube.com/watch?v=Eaz_o7cnlaM&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV&index=24 "Train TJBo to Suggest A Lunch Spot in Node-RED") 

## Flow

The flow consists of an inject node to inject a string, I'm hungry, a converse node to process the natural language with the Watson Conversation service, and a debug node to display the response from the Watson Conversation service.

![Suggest A Lunch Spot Flow](assets/flow.png) 

## Flow JSON

```
[{"id":"e2f6a954.630ff","type":"inject","z":"4f8a700b.20a01","name":"","topic":"","payload":"I'm hungry","payloadType":"str","repeat":"","crontab":"","once":false,"x":260,"y":280,"wires":[["e1ff962b.8a1a78"]]},{"id":"e1ff962b.8a1a78","type":"tjbot-converse","z":"4f8a700b.20a01","botId":"4275751d.01daf4","name":"","x":420,"y":280,"wires":[["b0e1b6b9.19843"]]},{"id":"b0e1b6b9.19843","type":"debug","z":"4f8a700b.20a01","name":"","active":true,"console":"false","complete":"response.object.output.text[0]","x":650,"y":280,"wires":[]},{"id":"4275751d.01daf4","type":"tjbot-config","z":"","botGender":"male","name":"TJBot","hasServo":false,"hasLED":false,"hasSpeaker":false,"hasMicrophone":false,"hasCamera":false,"speakerDeviceId":"plughw:0,0"}]

```

## Conversation Workspace JSON
```
{"name":"TJBot","created":"2017-08-22T03:21:40.581Z","intents":[{"intent":"find_lunch","created":"2017-08-22T03:21:54.635Z","updated":"2017-08-22T03:22:13.360Z","examples":[{"text":"I'm hungry","created":"2017-08-22T03:21:59.943Z","updated":"2017-08-22T03:21:59.943Z"},{"text":"Where should we go for lunch?","created":"2017-08-22T03:22:08.174Z","updated":"2017-08-22T03:22:08.174Z"},{"text":"What's for lunch?","created":"2017-08-22T03:22:13.360Z","updated":"2017-08-22T03:22:13.360Z"}],"description":null}],"updated":"2017-08-22T03:25:45.205Z","entities":[{"entity":"cuisine","values":[{"value":"indian","created":"2017-08-22T03:22:45.284Z","updated":"2017-08-22T03:22:45.284Z","metadata":null,"synonyms":[]},{"value":"american","created":"2017-08-22T03:22:37.395Z","updated":"2017-08-22T03:22:37.395Z","metadata":null,"synonyms":[]},{"value":"asian","created":"2017-08-22T03:22:42.962Z","updated":"2017-08-22T03:22:42.962Z","metadata":null,"synonyms":[]},{"value":"mexican","created":"2017-08-22T03:22:47.806Z","updated":"2017-08-22T03:22:47.806Z","metadata":null,"synonyms":[]},{"value":"chinese","created":"2017-08-22T03:22:40.818Z","updated":"2017-08-22T03:22:40.818Z","metadata":null,"synonyms":[]}],"created":"2017-08-22T03:22:34.708Z","updated":"2017-08-22T03:22:47.806Z","metadata":null,"description":null}],"language":"en","metadata":{"api_version":{"major_version":"v1","minor_version":"2017-05-26"}},"description":"","dialog_nodes":[{"title":null,"output":{},"parent":null,"context":null,"created":"2017-08-22T03:23:09.611Z","updated":"2017-08-22T03:23:21.222Z","metadata":null,"next_step":null,"conditions":"#find_lunch","description":null,"dialog_node":"node_1_1503372190019","previous_sibling":"Welcome"},{"title":null,"output":{"text":{"values":["Hello. How can I help you?"],"selection_policy":"sequential"}},"parent":null,"context":null,"created":"2017-08-22T03:23:02.428Z","updated":"2017-08-22T03:23:02.428Z","metadata":null,"next_step":null,"conditions":"welcome","description":null,"dialog_node":"Welcome","previous_sibling":null},{"title":null,"output":{"text":{"values":["I didn't understand. You can try rephrasing.","Can you reword your statement? I'm not understanding.","I didn't get your meaning."],"selection_policy":"sequential"}},"parent":null,"context":null,"created":"2017-08-22T03:23:02.428Z","updated":"2017-08-22T03:23:02.428Z","metadata":null,"next_step":null,"conditions":"anything_else","description":null,"dialog_node":"Anything else","previous_sibling":"node_1_1503372190019"},{"type":"response_condition","title":null,"output":{"text":{"values":["How about a noodle bowl at NoodleMe?","Five spice chicken at Spice Kit?"],"selection_policy":"random"}},"parent":"node_1_1503372190019","context":null,"created":"2017-08-22T03:24:23.962Z","updated":"2017-08-22T03:25:05.377Z","metadata":null,"next_step":null,"conditions":" @cuisine:asian","description":null,"dialog_node":"node_3_1503372264416","previous_sibling":"node_2_1503372201363"},{"type":"response_condition","title":null,"output":{"text":{"values":["Steak burrito at Chipotle. Don't forget the guac!","There are a ton of options at Julie's Kitchen."],"selection_policy":"sequential"}},"parent":"node_1_1503372190019","context":null,"created":"2017-08-22T03:25:08.190Z","updated":"2017-08-22T03:25:45.205Z","metadata":null,"next_step":null,"conditions":" true","description":null,"dialog_node":"node_4_1503372308641","previous_sibling":"node_3_1503372264416"},{"type":"response_condition","title":null,"output":{"text":{"values":["Sandwich at Cafe Venue?","Roast beef at Speciality's sounds good today!","You've got a couple of options at Focaccia Market and Bakery."],"selection_policy":"random"}},"parent":"node_1_1503372190019","context":null,"created":"2017-08-22T03:23:20.939Z","updated":"2017-08-22T03:24:20.945Z","metadata":null,"next_step":null,"conditions":" @cuisine:american","description":null,"dialog_node":"node_2_1503372201363","previous_sibling":null}],"workspace_id":"5cfd5a77-4c22-4001-8ad6-26e609415dd6","counterexamples":[],"learning_opt_out":false}
```

## Tips

* Don't forget to create a Watson Conversation service and use the service credentials in the TJBot configuration

## Extra Credit

* Add a listen and speak node to enable TJBot to respond to voice and speak out the recommendation
* Use the additional cuisine entity values to return additional recommendations
* Add additional entities to customize the items being recommended
	
## Resources

If this is your first time using [Node-RED](https://nodered.org/), check out the [docs](https://nodered.org/docs/) for the Getting Started guide.
