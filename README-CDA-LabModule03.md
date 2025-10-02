# Constrained Device Application (Connected Devices)

## Lab Module 03

Be sure to implement all the PIOT-CDA-\* issues (requirements) listed at PIOT-INF-03-001 - Lab Module 03.



### Description

What does your implementation do?

This implementation builds the complete simulation and management infrastructure for a Constrained Device Application (CDA). It creates data containers for sensors, actuators, and system performance metrics, then implements simulation tasks that generate realistic telemetry data for environmental sensors (temperature, humidity, pressure) and process actuation commands for HVAC and humidifier devices. The system includes adapter managers that coordinate sensor polling on scheduled intervals and route actuator commands to appropriate devices. At the center is the DeviceDataManager, which orchestrates all components, performs on-device analytics (such as triggering HVAC based on temperature thresholds), and manages data flow through callback mechanisms. The ConstrainedDeviceApp serves as the main entry point, initializing and controlling the lifecycle of the entire system.

How does your implementation work?

The implementation follows a layered architecture. At the data layer, ActuatorData, SensorData, and SystemPerformanceData classes provide structured containers inheriting from BaseIotData. The simulation layer includes BaseSensorSimTask and BaseActuatorSimTask base classes that encapsulate common functionality, with concrete implementations for specific devices (HumiditySensorSimTask, TemperatureSensorSimTask, PressureSensorSimTask, HumidifierActuatorSimTask, HvacActuatorSimTask). The management layer uses SensorAdapterManager with APScheduler to poll sensors at configurable intervals (default 60 seconds), generating telemetry and forwarding it via callback to DeviceDataManager. ActuatorAdapterManager validates incoming commands by checking location IDs and response flags before routing to the appropriate actuator. DeviceDataManager implements the IDataMessageListener interface to receive callbacks from all managers, caches the latest data, performs temperature-based analytics to trigger HVAC commands when thresholds are exceeded, and coordinates startup/shutdown of all subsystems. The application reads configuration from PiotConfig.props to enable/disable features and set operational parameters.



### Code Repository and Branch

URL: https://github.com/\[your-username]/piot-python-components/tree/labmodule03

(Replace with your actual repository URL)

### 

### UML Design Diagram(s)

(Note: Include your UML class diagrams showing the relationships between DeviceDataManager, SensorAdapterManager, ActuatorAdapterManager, and the simulation tasks. The diagrams should show the IDataMessageListener callback pattern and the inheritance hierarchies for BaseSensorSimTask and BaseActuatorSimTask.)


<img width="3241" height="1611" alt="UML_ LabModule03_CDA" src="https://github.com/user-attachments/assets/5493301d-8388-4da6-bc45-b1bd60718e94" />

### Unit Tests Executed

Data Tests:



test\_ActuatorData

test\_SensorData

test\_SystemPerformanceData

test\_BaseIotData

### 

### Simulation Tests:



test\_HumiditySensorSimTask

test\_PressureSensorSimTask

test\_TemperatureSensorSimTask

test\_HumidifierActuatorSimTask

test\_HvacActuatorSimTask



### Common Tests (from previous labs):



test\_ConfigUtilDefault

test\_ConfigUtilCustom



System Tests (from previous labs):



test\_SystemCpuUtilTask

test\_SystemMemUtilTask





Integration Tests Executed

System Integration Tests:



test\_SensorAdapterManager

test\_ActuatorAdapterManager



Application Integration Tests:



test\_DeviceDataManagerNoComms

test\_ConstrainedDeviceApp


