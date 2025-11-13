Constrained Device Application (Connected Devices)
Lab Module 08


Description

Lab Module 08 focused on implementing CoAP (Constrained Application Protocol) server connectivity for the Constrained Device Application (CDA). This module involved installing and configuring CoAP tools (Californium for Java testing and aiocoap for Python implementation), creating an asynchronous CoAP server adapter, implementing resource handlers for telemetry and actuator commands, and integrating the CoAP server into the DeviceDataManager for IoT communication using the CoAP protocol.


Code Repository and Branch

URL: https://github.com/ReubenComla/Readme-connected-devices/blob/main/README-CDA-LabModule08.md

Branch: https://github.com/ReubenComla/cda-python-components/tree/labmodule08

UML Design Diagram(s)
<img width="1024" height="1024" alt="GDA-UML-LabModule08" src="https://github.com/user-attachments/assets/eb25f26a-2edf-46cc-ac99-ae0056774e05" />





Tests Executed


Integration Tests


CDA Application Integration Test -CoAP Server

Launched full ConstrainedDeviceApp with CoAP server enabled
Verified AsyncCoapServerAdapter initialization in DeviceDataManager constructor
Validated CoAP server startup on startManager()
Confirmed resource registration:

/.well-known/core (resource discovery)
/PIOT/ConstrainedDevice/ActuatorCmd/HumidifierActuator (actuator commands)
/PIOT/ConstrainedDevice/SystemPerfMsg (observable system performance telemetry)
/PIOT/ConstrainedDevice/SensorMsg (observable sensor data)


Monitored system performance telemetry (CPU and memory utilization every 5 seconds)
Verified CoAP server stability during runtime
Validated graceful server shutdown on stopManager()
Confirmed clean event loop closure and exit code 0

CoAP Server Tests

testServerStartupAndResourceDiscovery()

⦁	Verified AsyncCoapServerAdapter created CoAP server context
⦁	Confirmed server binding to localhost:5683
⦁	Validated resource tree creation with aiocoap.resource.Site()
⦁	Verified WKCResource registration for discovery endpoint
⦁	Confirmed all resource handlers properly registered
⦁	Validated server readiness to receive requests
⦁	Tested resource discovery using Californium cf-client:

  java -jar cf-client-4.0.0-SNAPSHOT.jar -m GET coap://localhost:5683/.well-known/core

Successfully discovered all 4 registered resources
Response time: 75ms
Result: ✅ PASS

Configuration Tests

testConfigurationLoading()

⦁	Verified PiotConfig.props loaded from /home/rain/piot/cda-python-components/config/PiotConfig.props
⦁	Confirmed [Coap.GatewayService] section parsing
⦁	Validated host property: localhost
⦁	Confirmed port property: 5683
⦁	Verified enableCoapServer: True in [ConstrainedDevice] section
Result: PASS


Async Server Implementation Tests
test_initServer()
⦁	Verified resource.Site() root resource creation
⦁	Confirmed WKCResource registration for /.well-known/core
⦁	Validated AsyncUpdateActuatorResourceHandler instantiation with dataMsgListener
⦁	Verified AsyncGetSystemPerformanceResourceHandler creation
⦁	Confirmed AsyncGetTelemetryResourceHandler creation
⦁	Validated setTelemetryDataListener() callback registration
⦁	Confirmed setSystemPerformanceDataListener() callback registration
⦁	Verified "Created CoAP server with default resources" log message
Result: PASS

