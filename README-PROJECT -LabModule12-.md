Intelligent HVAC Control System with Adaptive Thresholds
(Connected Devices) - Lab Module 12


Description

Lab Module 12 focused on implementing an Intelligent HVAC Control System with Adaptive Thresholds. This capstone module involved integrating the Constrained Device Application (CDA) with Ubidots cloud platform using MQTT protocol, implementing real-time sensor data publishing (temperature, humidity, pressure), creating cloud-to-device communication infrastructure for actuator control, developing adaptive threshold management logic to prevent actuator chatter, and building a comprehensive dashboard for monitoring and manual control of HVAC thresholds. The system demonstrates distributed intelligence with edge-based decision making and cloud-based visualization.



Code Repository and Branch

URL: https://github.com/ReubenComla/cda-python-components

Branch: https://github.com/ReubenComla/cda-python-components/tree/labmodule12


UML Design Diagram





Tests Executed

Integration Tests
CDA Restart Test

Started CDA application: python3 programmingtheiot/cda/app/ConstrainedDeviceApp.py
Verified configuration loaded from PiotConfig.props
Confirmed sensor adapters initialized (Temperature, Humidity, Pressure)
Validated system performance manager started
Verified scheduler jobs added for 5-second telemetry intervals
Confirmed clean startup with no errors
Validated exit code 0 on shutdown

Result: ✅ PASS
CDA Connection Test

Verified MQTT client initialization with Ubidots credentials
Confirmed MQTT authentication enabled
Validated client ID: constraineddevice001
Tested connection to broker: things.ubidots.com:1883
Verified callback: "[Callback] Connected to MQTT broker. Result code: 0"
Confirmed subscriptions established to control topics
Validated keep-alive: 60 seconds

Result: ✅ PASS
Cloud Connection Test

Tested sensor data publishing to Ubidots cloud
Verified topics:

/v1.6/devices/constraineddevice001/tempsensor
/v1.6/devices/constraineddevice001/humiditysensor
/v1.6/devices/constraineddevice001/pressuresensor


Confirmed JSON payload format: {"value": <sensor_value>}
Validated MQTT QoS 0 transmission
Tested HVAC status publishing to hvac_status topic
Verified zero packet loss
Confirmed continuous 5-second publishing interval

Result: ✅ PASS
Device Connection Test

Verified Ubidots device: constraineddevice001 created
Confirmed 8 variables active:

tempsensor (live updates)
humiditysensor (live updates)
pressuresensor (live updates)
systemperfmsg (CPU/Memory metrics)
threshold_floor (threshold display)
threshold_ceiling (threshold display)
threshold_events (change log)
hvac_status (operational state)


Validated timestamps showing "a few seconds ago"
Tested dashboard widgets displaying real-time data
Confirmed device last activity: live connection

Result: ✅ PASS


Test Commands
CDA Restart Test
bashcd ~/piot/cda-python-components
python3 programmingtheiot/cda/app/ConstrainedDeviceApp.py
What to verify: Configuration loads, sensors initialize, no errors

CDA Connection Test
bash# CDA must be running from previous test
# Look for these lines in terminal output:
grep "Connected to MQTT broker" cda_startup.log
# Or just watch terminal for: "[Callback] Connected to MQTT broker. Result code: 0"
What to verify: Connection successful, Result code = 0

Cloud Connection Test
bash# CDA must be running
# Watch terminal for publishing messages every 5 seconds:
# "Published sensor data to topic: /v1.6/devices/constraineddevice001/tempsensor"
# "Published sensor data to topic: /v1.6/devices/constraineddevice001/humiditysensor"
# "Published sensor data to topic: /v1.6/devices/constraineddevice001/pressuresensor"
# "📊 Published HVAC Status: COOLING ACTIVE (value=2)"
What to verify: All sensors publishing, no errors

Device Connection Test
bash# In browser: Go to Ubidots → Devices → constraineddevice001
# Check all 8 variables show recent timestamps
# Check dashboard shows live data updating
What to verify: All variables show "a few seconds ago", dashboard widgets update
