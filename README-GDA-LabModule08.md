# Constrained Device Application (Connected Devices)

## Lab Module 08



### Description


Applications, implementing resource handlers for processing PUT requests (system performance and sensor data), creating an observable resource handler for actuator commands using the CoAP OBSERVE specification, and integrating the CoAP server into the DeviceDataManager for seamless IoT gateway operations. The implementation included resource tree management with hierarchical URI path structures, message acceptance and response code handling, JSON payload conversion using DataUtil, and proper server lifecycle management with MessageTracer interceptors for debugging. All components were successfully compiled and integrated with the DeviceDataManager to enable bi-directional communication between the Gateway Device Application and Constrained Device Applications through the CoAP protocol running on localhost:5683.




### UML diagram for LabModule05
<img width="1024" height="1024" alt="GDA-UML-LabModule08" src="https://github.com/user-attachments/assets/f9140d9e-d830-4760-9a0c-1a1b45610397" />



### 

### Code Repository and Branch

URL : https://github.com/ReubenComla/gda-java-components


Branch -https://github.com/ReubenComla/gda-java-components/tree/labmodule08

....



Reource Handler test

Resource Handler Tests
testUpdateSystemPerformanceResourceHandler()

Created UpdateSystemPerformanceResourceHandler instance
Verified CoapResource extension
Validated setDataMessageListener() method
Tested handlePUT() with valid JSON payload
Confirmed SystemPerformanceData deserialization from JSON
Verified handleSystemPerformanceMessage() callback invocation
Validated ResponseCode.CHANGED for successful PUT requests
Tested ResponseCode.BAD_REQUEST for invalid payloads
Confirmed ResponseCode.NOT_ACCEPTABLE when no listener set
Tested basic GET, POST, DELETE implementations
Result:  PASS

Integration Tests Executed

GDA Application Integration Test - CoAP Server

Launched full GatewayDeviceApp application
Verified CoapServerGateway initialization in DeviceDataManager
Validated CoAP server startup on startManager()
Confirmed resource handler registration (3 resources)
Monitored CoAP server stability during runtime
Verified server responds to discovery requests
Validated graceful server shutdown on stopManager()
Confirmed clean application exit with code 0
Result: PASS

Configuration Tests
testConfigurationLoading()

Verified PiotConfig.props loaded successfully
Confirmed [Coap.GatewayService] section parsing
Validated host property: localhost
Confirmed port property: 5683
Tested securePort property: 5684
Verified enableCoapServer: True in [GatewayDevice] section
Validated enableConfirmedMsgs configuration
Result: PASS












