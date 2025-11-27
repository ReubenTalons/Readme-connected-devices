# Constrained Device Application (Connected Devices)

## Lab Module 09



### Description





Applications implementing CoAP client functionality for communicating with Constrained Device Applications, including GET requests for resource discovery and data retrieval, POST requests for creating new resources, PUT requests for updating actuator commands and system configurations, DELETE requests for resource removal, and OBSERVE operations for real-time sensor data monitoring using the CoAP OBSERVE specification. The implementation included CoAP client connector integration with the DeviceDataManager, request/response handling with proper CoAP message codes, JSON payload serialization/deserialization using DataUtil, observer pattern implementation for continuous data streaming, and proper client lifecycle management with connection establishment and teardown. All components were successfully compiled and integrated with the DeviceDataManager to enable bi-directional communication between the Gateway Device Application and Constrained Device Applications through the CoAP protocol running on localhost:5683.









### UML diagram for LabModule09



### 

### Code Repository and Branch



Repository: https://github.com/ReubenComla/gda-python-components

Branch: https://github.com/ReubenComla/gda-python-components/tree/labmodule09





### Unit Test Executed





#### CoAP Client Connector Tests

#### testCoapClientConnector()



Created CoapClientConnector instance

Verified client initialization with host and port

Validated connectClient() method

Tested sendGetRequest() with valid resource path

Confirmed response handling for GET requests

Verified sendPostRequest() with JSON payload

Validated ResponseCode.CREATED for successful POST

Tested sendPutRequest() for actuator command updates

Confirmed ResponseCode.CHANGED for successful PUT requests

Tested sendDeleteRequest() for resource removal

Validated ResponseCode.DELETED for successful DELETE

Confirmed disconnectClient() cleanup

Result: ✅ PASS





#### testCoapObserver()



Created CoapClientConnector instance with observer support

Verified startObserver() registration

Validated continuous sensor data reception

Confirmed onLoad() callback invocation for each notification

Tested SensorData deserialization from CoAP notifications

Verified handleSensorMessage() callback with updated data

Validated observer cancellation with stopObserver()

Confirmed proper cleanup after observation







#### testGetRequest()



Initialized CoapClientConnector

Sent GET request to /PIOT/ConstrainedDevice/SensorMsg

Verified response code: ResponseCode.CONTENT

Confirmed JSON payload deserialization

Validated SensorData object creation

Tested multiple sequential GET requests

Result: ✅ PASS



#### testPostRequest()



Created ActuatorData instance with command

Serialized ActuatorData to JSON using DataUtil

Sent POST request to /PIOT/ConstrainedDevice/ActuatorCmd

Verified ResponseCode.CREATED response

Confirmed resource creation on CDA

Tested POST with invalid payload handling



testPutRequest()



Created ActuatorData with updated command value

Serialized to JSON payload

Sent PUT request to /PIOT/ConstrainedDevice/ActuatorCmd

Verified ResponseCode.CHANGED response

Confirmed actuator state update on CDA

Tested PUT request error handling

Result: ✅ PASS



testDeleteRequest()



Sent DELETE request to /PIOT/ConstrainedDevice/ActuatorCmd

Verified ResponseCode.DELETED response

Confirmed resource removal on CDA

Tested DELETE on non-existent resource

Validated ResponseCode.NOT\_FOUND handling

Result: ✅ PASS



Integration Tests Executed

#### GDA Application Integration Test - CoAP Client

#### testGatewayDeviceAppIntegration()



Launched full GatewayDeviceApp application

Verified CoapClientConnector initialization in DeviceDataManager

Validated CoAP client connection on startManager()

Confirmed observer registration for sensor data (3 resources)

Monitored continuous sensor data reception

Verified actuator command transmission via PUT requests

Validated system performance data retrieval via GET requests

Confirmed graceful client disconnection on stopManager()

Tested clean application exit with code 0

Result: ✅ PASS



#### testCoapClientServerCommunication()



Started CDA CoAP server (Lab Module 08)

Started GDA CoAP client (Lab Module 09)

Verified bidirectional communication

Tested GET request/response cycle

Validated POST request for actuator commands

Confirmed PUT request for data updates

Tested OBSERVE notifications for sensor data

Verified proper message formatting and parsing

Result: ✅ PASS



#### testDataUtilIntegration()



Verified DataUtil JSON conversion for SensorData

Confirmed ActuatorData serialization to JSON

Tested SystemPerformanceData deserialization

Validated proper type handling in payloads

Confirmed encoding/decoding consistency

Result: ✅ PASS







