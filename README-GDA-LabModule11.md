# Constrained Device Application (Connected Devices)

## Lab Module 11





### Description



Lab Module 11 focused on implementing cloud integration functionality for the Gateway Device Application (GDA), enabling end-to-end communication between the CDA, GDA, and Ubidots cloud service. This module involved creating cloud client interfaces and connectors, implementing MQTT-based cloud communication with TLS encryption, developing JSON data converters for cloud-compatible payloads, integrating connection listeners for asynchronous event handling, and establishing bidirectional data flow between edge devices and cloud services for sensor data collection and actuator command distribution.





### Code Repository and Branch



##### URL: https://github.com/ReubenComla/gda-java-components

##### Branch: https://github.com/ReubenComla/gda-java-components/tree/labmodule11





### UML Design Diagram(s)



<img width="1792" height="1015" alt="UML GDA lab 11" src="https://github.com/user-attachments/assets/3d7f74e6-2e52-414a-8740-7174defb723d" />









### 

## Tests Executed





1\. TimeAndValuePayloadDataTest (PIOT-GDA-11-002)

Purpose: Test JSON converters for TimeAndValuePayloadData

Command:

bash

mvn test -Dtest=TimeAndValuePayloadDataTest



Result: ✅ Tests run: 3, Failures: 0, Errors: 0, Skipped: 0







2\. Compilation Test

Purpose: Verify all code compiles without errors

Command:

bash

mvn clean compile

Result: ✅ BUILD SUCCESS - Compiling 40 source files





3\. CloudClientConnectorTest (PIOT-GDA-11-003)

Purpose: Test end-to-end cloud integration with Ubidots

Command:

bash

mvn test -Dtest=CloudClientConnectorTest

Result: ✅ Tests run: 1, Failures: 0, Errors: 0, Skipped: 0

•	Connected to Ubidots via MQTT with TLS

•	Published sensor data (Temperature: 92.0°F)

•	Published system performance data (CPU: 34.7%, Memory: 39.8%)

•	Subscribed to LED actuation topic

•	Received LED command from cloud

•	Data visible in Ubidots dashboard







4\. API Token Validation Test

Purpose: Verify Ubidots STEM token is valid

Command:

bash

curl -X GET -H "X-Auth-Token: BBUS-UilXOX7cDPjpPbKv32x8Zhu6UE3YDF" https://stem.ubidots.com/api/v2.0/devices/

Result: ✅ Authentication successful, valid token





5\. Network Connectivity Tests

Purpose: Verify network can reach Ubidots MQTT broker

Commands:

bash

nc -zv industrial.api.ubidots.com 8883

telnet industrial.api.ubidots.com 8883

Result: ✅ Port 8883 open and reachable





6\. Ubidots Dashboard Verification

Purpose: Visual confirmation of data in cloud

Result: ✅ Devices and variables visible at https://stem.ubidots.com/app/devices/







Summary:

•	Total Tests Run: 6

•	All Tests: PASSED ✅

•	Build Status: SUCCESS 

•	Cloud Integration: VERIFIED 










