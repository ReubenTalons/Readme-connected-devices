# Constrained Device Application (Connected Devices)

## Lab Module 10





### Description



Lab Module 10 focused on implementing advanced MQTT and CoAP protocol features for the Constrained Device Application (CDA), including performance benchmarking, security enhancements, and integration capabilities. This module involved conducting comprehensive performance tests for both MQTT (QoS levels 0, 1, 2) and CoAP (CON/NON message types), implementing TLS/SSL encryption for secure MQTT communication, configuring certificate-based authentication, adding intelligent actuator command handling via MQTT subscriptions, and preparing the foundation for intelligent edge messaging with threshold-based actuation between CDA and GDA components.





### Code Repository and Branch



##### URL: https://github.com/ReubenComla/cda-python-componentsBranch: 

https://github.com/ReubenComla/cda-python-components/tree/labmodule10



### UML Design Diagram(s)


<img width="2307" height="1207" alt="CDA-UML-DIAGRAM" src="https://github.com/user-attachments/assets/7ffcfd6c-dccf-4d4d-9944-e23b84aef298" />





### 

## Tests Executed



### Performance Tests

MQTT Client Performance Test

testConnectAndDisconnect()



Measured MQTT broker connection and disconnection timing

Result: 2,007.29 ms PASS



testPublishQoS0()



Tested 10,000 messages with QoS 0 (fire-and-forget)

Result: 1,491.95 ms (Baseline) PASS



testPublishQoS1()



Tested 10,000 messages with QoS 1 (at-least-once delivery)

Result: 3,049.08 ms (+104% vs QoS 0) PASS



testPublishQoS2()



Tested 10,000 messages with QoS 2 (exactly-once delivery)

Result: 4,134.72 ms (+177% vs QoS 0) PASS





CoAP Client Performance Test

testPostRequestNon()



Tested 100 POST requests with NON (non-confirmable) messages

Result: 100,304.06 ms (Baseline) PASS



testPostRequestCon()



Tested 100 POST requests with CON (confirmable) messages

Result: 90,993.09 ms (9.3% faster than NON) PASS





#### Security Configuration Tests

TLS Certificate Generation and Configuration

testCertificateGeneration()



Generated CA certificate and key using OpenSSL

Generated server certificate signed by CA

Common Name: localhost, Validity: 730 days

Result: PASS



testMosquittoTLSConfiguration()



Configured Mosquitto with TLS on port 8883

Created /etc/mosquitto/conf.d/tls.conf

Set proper file permissions for certificates

Verified Mosquitto listening on ports 1883 and 8883

Result: PASS



testMosquittoTLSCommandLine()



Tested encrypted pub/sub with mosquitto\_sub and mosquitto\_pub

Command: mosquitto\_sub -h localhost -p 8883 --cafile ~/mosquitto-certs/server.crt -t "test/secure" -v

Verified message "Hello TLS MQTT!" received over encrypted channel

Result: PASS





### Integration Tests

CDA MQTT TLS Implementation

testMqttClientTLSConnection()



Added TLS support to MqttClientConnector.py

Configured to use SSL with self-signed certificates

Verified connection to port 8883 with encryption enabled

Tested certificate loading from ./certs/ca.crt

Result: PASS





Actuator Command Handling

testActuatorDataCallback()



Created test file: test\_DeviceDataManagerCallback.py

Tested DeviceDataManager actuator command processing

Sent HVAC actuator command (COMMAND\_ON, value=52)

Verified command routing to ActuatorAdapterManager

Confirmed actuator simulation activation

Result: PASS





#### MQTT Actuator Command Subscription

testActuatorCmdPubSub()



Updated MqttClientConnector to auto-subscribe to actuator commands

Implemented onActuatorCommandMessage() callback

Verified automatic subscription in onConnect() (MID: 2)

Tested ActuatorData JSON conversion and message handling

Removed wait\_for\_publish() to prevent deadlock

Result: PASS





#### CDA Application Integration

testCDAWithSimulatedSensors()



Configured CDA with MQTT client and simulated sensors

Verified sensor data generation every 5 seconds (humidity, pressure, temperature)

Confirmed temperature threshold monitoring (floor: 18.0°C, ceiling: 20.0°C)

Validated automatic HVAC actuator triggering

Tested with TLS encryption enabled

Result:  PASS





#### Configuration Tests

testTLSConfiguration()



Verified CDA PiotConfig.props TLS settings

Confirmed enableCrypt = True and certFile = ./certs/ca.crt

Validated certificate file existence

Result: PASS



testCertificateDistribution()



Verified certificates copied to CDA project: ~/piot/cda-python-components/certs/

Verified certificates copied to GDA project: ~/piot/gda-java-components/certs/

Verified certificates copied to Mosquitto: /etc/mosquitto/

Confirmed proper file permissions and ownership

Result: PASS













### 



