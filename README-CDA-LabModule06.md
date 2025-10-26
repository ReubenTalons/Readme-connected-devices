# Constrained Device Application (Connected Devices)

## Lab Module 06





### Description



Lab Module 06 focused on implementing MQTT (Message Queuing Telemetry Transport) client connectivity for the Constrained Device Application (CDA). This module involved creating an MQTT client connector, implementing publish/subscribe functionality, adding event callbacks, and integrating the MQTT client into the DeviceDataManager for seamless IoT communication.





### Code Repository and Branch

### 





### UML Design Diagram(s)











### Tests Executed











Integration Tests
CDA Application Integration Test -
---



Launched full ConstrainedDeviceApp

Verified MQTT client initialization in DeviceDataManager constructor

Validated automatic MQTT connection on startManager()

Confirmed subscription to CDA\_ACTUATOR\_CMD\_RESOURCE topic

Monitored system performance telemetry (CPU and memory utilization)

Verified MQTT connection stability during runtime

Validated automatic unsubscribe on stopManager()

Confirmed clean MQTT disconnection on application shutdown

Verified exit code 0 (clean shutdown)

Result: ✅ PASS (67 seconds runtime)





Connection Tests

testConnectAndDisconnect()
---



Verified MQTT client connection to broker (localhost:1883)

Maintained connection for keepAlive period (65 seconds)

Verified clean disconnection from broker

Validated onConnect() callback execution

Validated onDisconnect() callback execution

Result: ✅ PASS (65.120s)















