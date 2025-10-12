# Constrained Device Application (Connected Devices)

## Lab Module 04



### Description

Lab Module 04 implements a comprehensive data emulation framework for IoT sensor and actuator management using the Sense HAT emulator. The solution enables dynamic generation of time-series environmental sensor data (temperature, humidity, and pressure) and supports emulated actuation through LED display control. The system is designed with flexibility in mind, supporting three operational modes: simulator (generated data), emulator (Sense HAT GUI), and hardware (physical I2C sensors on Raspberry Pi). The ActuatorAdapterManager dynamically routes actuator commands to the appropriate emulator tasks (Humidifier, HVAC, LED Display), which display visual feedback on the Sense HAT's 8x8 LED matrix by scrolling text messages like "HUMIDIFIER ON: 50.0C". The SensorAdapterManager uses a background scheduler to poll sensors at configurable intervals (default 5 seconds), collecting environmental telemetry data and distributing it throughout the system to registered listeners for processing, storage, or cloud transmission





What does your implementation do?

This implementation creates a complete IoT data emulation system that simulates environmental sensors and actuators using the Sense HAT emulator. The system collects real-time sensor data for temperature, humidity, and pressure, then displays this information and actuator commands visually on an 8x8 LED matrix display. It provides three flexible operational modes: a simulator mode that generates synthetic data for testing without hardware, an emulator mode that uses the Sense HAT GUI for development on standard computers, and a hardware mode that communicates directly with physical sensors via I2C on a Raspberry Pi.



How does your implementation work?

The implementation leverages a configuration-driven architecture where PiotConfig.props determines which sensor and actuator tasks to load at runtime through three boolean flags: enableEmulator (Sense HAT GUI), enableSenseHAT (physical I2C hardware), and enableSimulator (generated data). When the SensorAdapterManager initializes, it reads these configuration flags using ConfigUtil and calls \_initEnvironmentalSensorTasks(), which uses Python's import\_module() function to dynamically load the appropriate sensor task classes without hardcoding dependencies.

### 

### UML diagram for LabModule04



### 

### Code Repository and Branch

https://github.com/ReubenComla/cda-python-components

Branch - https://github.com/ReubenComla/cda-python-components/tree/labmodule03



### Unit Tests Executed



\* HumiditySensorEmulatorTaskTest

\* PressureSensorEmulatorTaskTest

\* TemperatureSensorEmulatorTaskTest

\* HumidifierEmulatorTaskTest

\* HvacEmulatorTaskTest

\* LedDisplayEmulatorTaskTest



### Integration Tests Executed

\* test\_SenseHatEmulatorQuick

\* test\_HumidityEmulatorTask

\* test\_PressureEmulatorTask

\* test\_TemperatureEmulatorTask

\* test\_HumidifierEmulatorTask

\* test\_HvacEmulatorTask

\* test\_LedDisplayEmulatorTask

\* test\_ActuatorEmulatorManager

\* test\_SensorEmulatorManager

\* test\_EmbeddedSensorAdapter

\* SystemPerformanceManagerTest

\* DeviceDataManagerNoCommsTest

