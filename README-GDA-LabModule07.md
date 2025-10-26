# Constrained Device Application (Connected Devices)

## Lab Module 07



### Description



Lab Module 07 focused on implementing MQTT (Message Queuing Telemetry Transport) client connectivity for the Gateway Device Application (GDA) using Java. This module involved creating a robust MQTT client connector using the Eclipse Paho Java library, implementing publish/subscribe messaging capabilities, adding comprehensive event callbacks for connection lifecycle management, and integrating the MQTT client into the DeviceDataManager for seamless IoT gateway operations. The implementation included connection management with automatic reconnection, topic-based message routing, quality of service (QoS) level handling, and proper resource cleanup. All components were tested using JUnit integration tests to validate connection stability, message delivery, and callback execution. The MQTT client connector was designed to work with the synchronous MqttClient for reliable blocking operations during testing and initial deployment. This lab established the foundation for bi-directional communication between the Gateway Device Application and Constrained Device Applications through a Mosquitto MQTT broker running on localhost:1883.











### UML diagram for LabModule07

<img width="2237" height="1682" alt="GDA_UML_LABMODULE07" src="https://github.com/user-attachments/assets/899b7b8f-9bbd-427b-be61-9bb758a6ebdc" />




### 

### Code Repository and Branch

https:https://github.com/ReubenComla/gda-java-components

Branch - https://github.com/ReubenComla/gda-java-components/tree/Labmodule07
....





### Connection Tests Executed







Verified MQTT client connection to broker (tcp://localhost:1883)

Validated generated client ID assignment

Tested connection attempt when already connected (expected warning)

Maintained connection for keepAlive period (65 seconds)

Verified clean disconnection from broker

Tested disconnection attempt when already disconnected (expected warning)

Validated connectComplete() callback execution

Result: ✅ PASS (~70 seconds)









### Integration Tests Executed



GDA Application Integration Test 



Launched full GatewayDeviceApp application

Verified MQTT client initialization in DeviceDataManager

Validated automatic MQTT connection on startManager()

Confirmed subscription to 4 topics (GDA and CDA message resources)

Monitored MQTT connection stability during 65-second runtime

Verified automatic unsubscribe on stopManager()

Confirmed clean MQTT disconnection on application shutdown

Validated exit code 0 (clean shutdown)

Result: ✅ PASS (65 seconds runtime)

