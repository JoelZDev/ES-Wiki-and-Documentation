**Using the WLAN & MQTT Module on esp32**

- Author: David Lotz 
- Last Edited: 18.11.2021 
- Include the esp32_wlan.h and esp32_mqtt.h Header-Files before trying to use any functions. Moreover, these modules rely on the PubSubClient Library by Nick O`Leary, so this must be included in your project, too. 
- Execution-order from top to bottom: 


**bool connectWiFi(ssid, password)**
- This function establishes a wireless LAN connection, using the WiFi.h library from Arduino. It tries to connect to the specified WLAN, using given ssid and password. 
- Arguments "ssid" and "password" are both of const char* type, and are preferably created as global variables in a "//WLAN connection settings" section of the main.cpp file. 
- If the connection was a success, true is returned. 


**bool setupMQTT(mqtt_server, mqtt_port)**
- This function sets up the current MQTT settings, depositting the server address and wanted port for later connections in the client of the MQTT module. 
- Argument "mqtt_server" is of const char* type, "mqtt_port" is of uint16_t type. They are preferably created as global variables in a "//MQTT connection settings" section of the main.cpp file. 
- Returns true if settings were made successfully. 

 
**bool reconnect(client_name)**
- This function tries to connect to the Broker specified by calling the setupMQTT() function. 
- Argument "client_name" is of char* type, and is preferably created as global variable in a "//MQTT connection settings" section of the main.cpp file. 
- Returns true if the connection was a success. 


**bool subscribeTo(topic)**
- This function is used to subscribe the client to a specified topic. 
- Argument "topic" is of const char* type, and is preferably created as global variable in a "//MQTT connection settings" section of the main.cpp file. 
- It is strongly recommended to use different topics for either publishing or listening to messages, as a message published on a topic that is also listened to, results in this client receiving its own message. Whether or not the client reacts to such a message must be specified in the callback() function.
- Returns true if the subscription was a success. 


**bool publishMsg(topic, payload)**
- This function is used to listen to publish a message on a specified topic. 
- Arguments "topic" and "payload" are of const char* type. 
- Returns true if publishing the message was a success.


**bool setCallback(callback)**
- This function sets the message callback function.
- Argument "callback" is a pointer to a message callback function called when a message arrives for a subscription created by this client.
- Returns true if setting the callback function was a success.


**listen()**
- This function is used to listen to all topics that this client is subscribed to. 
- When the client should be waiting for incoming messages, this must be called() continuously inside a while-loop. 
- If any message on any subscribed topic is received, the callback() function inside the MQTT module is called and any code inside it is executed. 



