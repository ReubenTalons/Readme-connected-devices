# Constrained Device Application (Connected Devices)

## Lab Module 05



### Description



Lab Module 05 focuses on implementing local data persistence and JSON data conversion capabilities for the Constrained Device Application (CDA). This module introduces integration with time-series databases (InfluxDB) and key-value stores (Redis) to enable data storage and retrieval. Additionally, the module implements JSON serialization/deserialization utilities to facilitate data exchange between the CDA and Gateway Device Application (GDA).











### UML diagram for LabModule05



### 

### Code Repository and Branch

https://github.com/ReubenComla/da-python-components

Branch - https://github.com/ReubenComla/cda-python-components/tree/labmodule05Unit Tests Executed

....





### Unit Tests Executed

test\_DataUtil.py



testActuatorDataConversionsFromJson - PASSED ✅

testActuatorDataConversionsFromObject - PASSED ✅

testSensorDataConversionsFromJson - PASSED ✅

testSensorDataConversionsFromObject - PASSED ✅

testSystemPerformanceConversionsFromJson - PASSED ✅

testSystemPerformanceDataConversionsFromObject - PASSED ✅



Summary: Ran 6 tests in 0.022s - ALL PASSED ✅











### Integration Tests Executed

test\_SystemPerformanceManager.py



Integration test for SystemPerformanceManager - PASSED ✅

Duration: 60.023 seconds



test\_DataIntegration.py



testReadActuatorDataFromGdaDataPath - PASSED ✅

testReadSensorDataFromGdaDataPath - PASSED ✅

testReadSystemPerformanceDataFromGdaDataPath - PASSED ✅

testWriteActuatorDataToCdaDataPath - PASSED ✅

testWriteSensorDataToCdaDataPath - PASSED ✅

testWriteSystemPerformanceDataToCdaDataPath - PASSED ✅



Summary: Ran 6 tests in 0.031s - ALL PASSED ✅

