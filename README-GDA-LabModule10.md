# Constrained Device Application (Connected Devices)

## Lab Module 10



### Description





Lab Module 10 focused on implementing performance benchmarking, security enhancements, and intelligent messaging capabilities for the Gateway Device Application (GDA). Applications implementing MQTT client functionality with TLS encryption support, performance testing across multiple QoS levels, CoAP client performance benchmarking with CON/NON message types, certificate-based authentication for secure broker connections, and integration with the DeviceDataManager for receiving sensor data from Constrained Device Applications. The implementation included MQTT client TLS configuration with SSL certificate handling, actuator command publishing to CDA topics, sensor data subscription and processing, and proper client lifecycle management with encrypted connections running on localhost:8883 for secure communications.











### UML diagram for LabModule09

<img width="2090" height="1562" alt="GDA-UML-DIAGRAM" src="https://github.com/user-attachments/assets/d6270f30-4a5b-4e1c-a7e8-3473dfd19184" />


### 

### Code Repository and Branch



Repository: https://github.com/ReubenComla/gda-java-components

Branch: https://github.com/ReubenComla/gda-java-components/tree/labmodule10



### 



## Tests Executed



#### Performance Tests

MQTT Client Performance Test

testConnectAndDisconnect()



Measured MQTT broker connection and disconnection timing

Verified client initialization and cleanup

Validated connection establishment to localhost:1883





testPublishQoS0()



Tested publishing 10,000 messages with QoS 0 (at most once delivery)

Verified fire-and-forget message transmission





testPublishQoS1()



Tested publishing 10,000 messages with QoS 1 (at least once delivery)

Verified acknowledgment-based delivery





testPublishQoS2()



Tested publishing 10,000 messages with QoS 2 (exactly once delivery)

Verified 4-way handshake protocol







### CoAP Client Performance Test

#### testPostRequestCon()



Tested 10,000 POST requests with CON (Confirmable) messages

Verified acknowledgment reception from CDA CoAP server



#### testPostRequestNon()



Tested 10,000 POST requests with NON (Non-confirmable) messages

Verified fire-and-forget CoAP transmission







#### Security Configuration Tests

TLS Certificate Configuration

testCertificateDistribution()



Verified certificates copied to GDA project: ~/piot/gda-java-components/certs/

Confirmed ca.crt and server.crt present in certs directory

Validated certificate paths in PiotConfig.props

Result: PASS



testGDAConfigurationTLS()



Verified PiotConfig.props TLS settings in \[Mqtt.GatewayService] section

Confirmed enableCrypt = True

Validated certFile = ./certs/ca.crt

Verified securePort = 8883

Result: ✅ PASS



### 

### Integration Tests

GDA Application Integration Test - MQTT Client

testMqttClientConnection()



Launched GatewayDeviceApp application

Verified MqttClientConnector initialization in DeviceDataManager

Validated MQTT client connection to broker: tcp://localhost:1883

Confirmed subscription to CDA topics:



PIOT/GatewayDevice/MgmtStatusMsg

PIOT/ConstrainedDevice/ActuatorResponse

PIOT/ConstrainedDevice/SensorMsg

PIOT/ConstrainedDevice/SystemPerfMsg





#### Verified connection success callback

Result: ✅ PASS



testCoAPServerStart()



Verified CoAP server started successfully on port 5683

Confirmed server ready to accept client connections

Validated server resource registration

Result: ✅ PASS



testDeviceDataManagerStart()



Confirmed DeviceDataManager started successfully

Verified all managers initialized properly

Validated "GDA started successfully" message

Result: ✅ PASS



#### 

#### GDA CoAP Server Integration

testCoAPServerResourceHandlers()



Verified CoAP server resource handlers initialized:



GetActuatorCommandResourceHandler (observable resource)

UpdateSystemPerformanceResourceHandler





Confirmed resource chains added:



PIOT/ConstrainedDevice/ActuatorCmd

PIOT/ConstrainedDevice/SensorMsg

PIOT/ConstrainedDevice/SystemPerfMsg





Validated default CoAP resources initialized

Result: ✅ PASS





#### Configuration Tests

testMQTTConfiguration()



Verified MQTT client enabled in \[GatewayDevice] section

Confirmed enableMqttClient = True

Validated broker connection settings (host: localhost, port: 1883)

Result: ✅ PASS



testCoAPConfiguration()



Verified CoAP server enabled: enableCoapServer = True

Verified CoAP client enabled: enableCoapClient = True

Confirmed server listening on port 5683

Result: ✅ PASS









