# TJBot Node-RED Skills

This project contains resources for use in training the TJBot skills using Node-RED.

## Day 1 - Setting up your TJBot to use Node-RED

Resources: [GitHub](1-setup) | [Medium](https://medium.com/@jeancarlbisson/setting-up-your-tjbot-to-use-node-red-df94ff94a114) | YouTube [Part 1](https://www.youtube.com/watch?v=J23LdKeghBg&index=1&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV), [Part 2](https://www.youtube.com/watch?v=xLfpcJYa8eI&index=2&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV), [Part 3](https://www.youtube.com/watch?v=EKmSuDYbzhE&index=3&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV), [Part 4](https://www.youtube.com/watch?v=Je9VJv_sxt8&index=4&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV)

Today we'll learn how to flash the Raspbian Jessie with Desktop image to a microSD card; enable SSH, VNC, and the Camera interfaces, set an SSH password, and upgrade Node.js and Node-RED to the latest version; install a Node-RED package containing nodes that can be used with the TJBot; and create a profile for TJBot to use as we train it with different abilities to perform. 

## Day 2 - Wave

Resources: [GitHub](2-wave) | [Medium](https://medium.com/@jeancarlbisson/train-tjbot-to-wave-in-node-red-62826d269ba5) | [YouTube](https://www.youtube.com/watch?v=uE8pvLttipU&index=5&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV)

![Wave Flow](2-wave/assets/flow.png)

Today we'll train TJBot to wave using the wave node.

## Day 3 - Shine

Resources: [GitHub](3-shine) | [Medium](https://medium.com/@jeancarlbisson/train-tjbot-to-shine-led-in-node-red-918fcc6d844d) | [YouTube](https://www.youtube.com/watch?v=8htZriltJuc&index=6&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV)

![Shine Flow](3-shine/assets/flow.png)

Today we'll train TJBot to shine the LED the color red using the shine node.

## Day 4 - Pulse

Resources: [GitHub](4-pulse) | [Medium](https://medium.com/@jeancarlbisson/train-tjbot-to-pulse-the-led-in-node-red-ca044b2ef63) | [YouTube](https://www.youtube.com/watch?v=AkOWGQjlaXk&index=7&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV)

![Pulse Flow](4-pulse/assets/flow.png)

Today we'll train TJBot to pulse the LED the color red using the shine node.

## Day 5 - Listen

Resources: [GitHub](5-listen) | [Medium](https://medium.com/@jeancarlbisson/train-tjbot-to-listen-in-node-red-ab9500768c52) | [YouTube](https://www.youtube.com/watch?v=AFNUa7y5XeU&index=8&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV)

![Listen Flow](5-listen/assets/flow.png)

Today we’ll train TJBot to listen using the microphone and the Watson Speech to Text service.

## Day 6 - Speak

Resources: [GitHub](6-speak) | [Medium](https://medium.com/@jeancarlbisson/train-tjbot-to-speak-in-node-red-a424d801d5d3) | [YouTube](https://www.youtube.com/watch?v=cOd2FWa4eOw&index=9&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV)

![Speak Flow](6-speak/assets/flow.png)

Today we’ll train TJBot to speak using the speaker and the Watson Text to Speech service.

## Day 7 - See

Resources: [GitHub](7-see) | [Medium](https://medium.com/@jeancarlbisson/train-tjbot-to-see-in-node-red-1821dd0513f6) | [YouTube](https://www.youtube.com/watch?v=8XSo_CaY0rs&index=10&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV)

![See Flow](7-see/assets/flow.png)

Today we’ll train TJBot to see using the Raspberry Pi camera and the Watson Visual Recognition service.

## Day 8 - Analyze Tone

Resources: [GitHub](8-analyze-tone) | [Medium](https://medium.com/@jeancarlbisson/train-tjbot-to-analyze-the-tone-in-node-red-1bd21be75917) | [YouTube](https://www.youtube.com/watch?v=VuopoVT0uCo&index=11&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV)

![Analyze Tone Flow](8-analyze-tone/assets/flow.png)

Today we’ll train TJBot to analyze three types of tones using the Watson Tone Analyzer service.

## Day 9 - Translate

Resources: [GitHub](9-translate) | [Medium](https://medium.com/@jeancarlbisson/train-tjbot-to-translate-in-node-red-dabf272ad9eb) | [YouTube](https://www.youtube.com/watch?v=oIM4dp-mctE&index=12&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV)

![Translate Flow](9-translate/assets/flow.png)

Today we’ll train TJBot to translate a greeting (for example from English to Spanish) using the Watson Language Translator service.

## Day 10 - Converse

Resources: [GitHub](10-converse) | [Medium](https://medium.com/@jeancarlbisson/train-tjbot-to-converse-in-node-red-b46bf765fd4a) | [YouTube](https://www.youtube.com/watch?v=IxQN3CLVt88&index=13&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV)

![Converse Flow](10-converse/assets/flow.png)

Today we’ll train TJBot to respond using the converse node and the Watson Conversation service.

## Day 11 - Analyze Emotion

Resources: [GitHub](11-analyze-emotion) | [Medium](https://medium.com/@jeancarlbisson/train-tjbot-to-analyze-emotion-in-node-red-47a8e78b2cb2) | [YouTube](https://www.youtube.com/watch?v=ggED7bpr2dg&index=14&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV)

![Analyze Emotion](11-analyze-emotion/assets/flow.png)

Today we’ll train TJBot to analyze the emotions of an utterance and light the LED one of five colors representing the emotions anger, disgust, fear, joy, and sadness.

## Day 12 - Identify Language

Resources: [GitHub](12-identify-language) | [Medium](https://medium.com/@jeancarlbisson/train-tjbot-to-identify-language-in-node-red-34dee98da592) | [YouTube](https://www.youtube.com/watch?v=RNiLn9WV3a0&index=15&list=PLddOPkVMz1dtN3I_4JKava4GBLLXuUevV)

![Identify Language](12-identify-language/assets/flow.png)

Today we’ll train TJBot to identify what language a greeting is in using the translate node and the Watson Language Translator service.

## Day 13 - Identify Language and Translate

coming tomorrow...

## License

This code is licensed under Apache 2.0. Full license text is available in [LICENSE](LICENSE).
