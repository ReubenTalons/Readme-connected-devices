Constrained Device Application (Connected Devices)
Lab Module 05


Description

Lab Module 05 focuses on implementing local data persistence and JSON data conversion capabilities for the Constrained Device Application (CDA). This module introduces integration with time-series databases (InfluxDB) and key-value stores (Redis) to enable data storage, retrieval, and message passing between the CDA and Gateway Device Application (GDA). The lab implements JSON serialization/deserialization utilities using Python's json library to facilitate seamless data exchange. Additionally, the SystemPerformanceManager is updated to create SystemPerformanceData instances and integrate callback listeners for data message handling. Key objectives include installing and configuring InfluxDB with four data buckets, securing Redis with password authentication, implementing bidirectional JSON conversions for ActuatorData, SensorData, and SystemPerformanceData, and validating all implementations through comprehensive unit and integration testing. This module establishes the foundation for data persistence and cross-application communication in the IoT system.RetryClaude can make mistakes. Please double-check responses. Sonnet 4.5


Code Repository and Branch
URL: https://github.com/ReubenComla/cda-python-components/tree/labmodule05


UML Design Diagram

<img width="1536" height="1024" alt="UML_CDA_LAB_Module05" src="https://github.com/user-attachments/assets/24773e81-0ad4-4e27-8b14-8f03b1fb79c9" />


Unit Tests Executed
test_DataUtil.py

testActuatorDataConversionsFromJson - PASSED 
testActuatorDataConversionsFromObject - PASSED 
testSensorDataConversionsFromJson - PASSED 
testSensorDataConversionsFromObject - PASSED 
testSystemPerformanceConversionsFromJson - PASSED 
testSystemPerformanceDataConversionsFromObject - PASSED 
Summary: 6/6 tests passed in 0.022s 


Integration Tests:
test_SystemPerformanceManager.py

SystemPerformanceManager integration test - PASSED 
Duration: 60.023 seconds
Collected CPU utilization (0% - 43%)
Collected memory utilization (54.6% - 54.8%)
Created SystemPerformanceData objects every 5 seconds
Invoked callback listener 12 times successfully

test_DataIntegration.py

testReadActuatorDataFromGdaDataPath - PASSED 
testReadSensorDataFromGdaDataPath - PASSED 
testReadSystemPerformanceDataFromGdaDataPath - PASSED 
testWriteActuatorDataToCdaDataPath - PASSED 
testWriteSensorDataToCdaDataPath - PASSED 
testWriteSystemPerformanceDataToCdaDataPath - PASSED 
Summary: 6/6 tests passed in 0.031s 


Infrastructure Tests:


InfluxDB Connection Test

Successfully connected to InfluxDB at localhost:8086 
Wrote test temperature data (22.5°C from room1/sensor01) 
Retrieved and verified stored data 

Redis Connection Test

Successfully connected to Redis at localhost:6379 
Authenticated with password successfully 
Stored sensor data with 1-hour expiration 
Retrieved data successfully 
Verified Redis server info (version 7.0.15) 
RetryClaude can make mistakes. Please double-check responses. Sonnet 4.5
