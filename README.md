# home-assistant-blueprints
This repository contains my custom [Home Assistant](https://www.home-assistant.io) blueprints.

---

## 📘 Available Blueprints

### Detect stale temperature sensors
This blueprint checks for stale sensors every x-hours for a specific 'last updated' time of an entity. (to detect an empty battery before the sensor is marked as unavailable) <br />
For many sensors the battery state is not reliable or frequently updated, so a device may be stale without knowing it. This is the case for multiple sensors, like: LYWSD03MMC temperaturesensor or the HHCCJCY01 plantsensor.


[![Import Blueprint into Home Assistant](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https://raw.githubusercontent.com/iq9003/home-assistant-blueprints/main/blueprints/automation/iq9003/motion_light.yaml)

---
# Example Automations
<img src="images/CreateAutomation.png" width="500">

### Notification example:
```action: persistent_notification.create
metadata: {}
data:
  title: Stale Sensor Alert
  message: >-
    No sensor "{{ sensor_name }}" in device model "{{ device_model }}"        
    {% if area_name != 'Unknown Area' %}(Area: {{ area_name }}){% endif
    %}         has updated in the last {{ stale_minutes }} minutes. -- Sensor(s)
    "{{ sensor_name }}" in {% if area_name != 'Unknown Area' %}(Area(s): {{
    area_name }}){% endif %} not updated in the last {{ stale_minutes }}
    minutes.
```    
