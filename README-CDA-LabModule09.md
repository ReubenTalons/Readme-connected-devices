# Constrained Device Application (Connected Devices)

## Lab Module 09





### Description



Lab Module 09 focused on implementing CoAP (Constrained Application Protocol) client connectivity for the Constrained Device Application (CDA). This module involved creating both synchronous and asynchronous CoAP client connectors, implementing full REST-like operations (GET, PUT, POST, DELETE), adding resource discovery functionality, implementing OBSERVE capabilities for real-time resource monitoring, and integrating both CoAP clients into the DeviceDataManager for comprehensive IoT communication using the CoAP protocol.





### Code Repository and Branch



##### URL: https://github.com/ReubenComla/cda-python-components

##### 

##### Branch: https://github.com/ReubenComla/cda-python-components/tree/labmodule09



### UML Design Diagram(s)











### Tests Executed











## Integration Tests

## 



## CDA Application Integration Test -CoAP Server



Verified AsyncCoapClientConnector initialization in DeviceDataManager constructor

Validated CoAP client context creation and event loop initialization

Confirmed client connection target: coap://127.0.0.1:5683/

Monitored system performance telemetry (CPU and memory utilization every 5 seconds)

Verified CoAP client stability during runtime

Validated graceful client shutdown on stopManager()

Confirmed clean event loop closure and exit code 0





## CoAP Client Tests

#### testClientInitialization()



Verified CoapClientConnector created HelperClient instance

Confirmed AsyncCoapClientConnector created aiocoap client context

Validated hostname resolution: localhost → 127.0.0.1

Verified client connection to server at localhost:5683

Confirmed asyncio event loop initialization for async client

Validated client readiness to send requests





#### testDiscoveryRequest()



Tested resource discovery using .well-known/core endpoint

Verified both sync (coapthon3) and async (aiocoap) discovery implementations

Confirmed discovery response received and parsed

Validated list of available server resources returned





#### testPutRequest()



Tested PUT requests for updating resources on CoAP server

Verified payload encoding and transmission

Confirmed both CON and NON message type support

Validated server response reception and logging

Tested SensorData transmission in JSON format





#### testGetRequest()



Tested GET requests for retrieving data from CoAP server

Verified both CON (confirmable) and NON (non-confirmable) message types

Confirmed request creation with proper CoAP codes

Validated response handling and payload parsing

Tested ActuatorData retrieval and JSON decoding





#### testPostRequest()



Tested POST requests for creating resources on CoAP server

Verified payload attachment to POST requests

Confirmed proper request formatting and token generation

Validated callback-based response handling

Tested SensorData creation via POST





#### testDeleteRequest()



Tested DELETE requests for removing resources from CoAP server

Verified both CON and NON DELETE message types

Confirmed request creation and transmission

Validated response handling (including cases where server doesn't support DELETE)

Tested cleanup and error handling





## Configuration Tests



#### testConfigurationLoading()



Verified PiotConfig.props loaded from /home/rain/piot/cda-python-components/config/PiotConfig.props

Confirmed \[Coap.GatewayService] section parsing

Validated host property: localhost

Confirmed port property: 5683

Verified enableCoapClient: True in \[ConstrainedDevice] section



Result: ✅ PASS

