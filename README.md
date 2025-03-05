# Motion Sensor Project (Package-Based)

This **Motion Sensor** configuration is published as an **ESPHome package**, allowing you to include it directly from GitHub without copying YAML files locally.

## Usage
In your **own** ESPHome YAML, add:
```yaml
esphome:
  name: ${device_name}

packages:
  motion_sensor:
    url: https://github.com/DBR-it/Motion-sensors
    ref: main
    files:
      - motion_sensor.yaml
```

### How It Works
- The **`packages`** section pulls the YAML configuration directly from GitHub.
- **`my_motion_sensor`** is the custom name for your device in Home Assistant.
- The configuration is updated automatically based on the `refresh` interval (e.g., `refresh: 1d`).

## Customizing the Sensor
You can override default **substitutions** in your local YAML file:
```yaml
substitutions:
  device_name: "my_custom_motion_sensor"
  sensor_name_north: "North Motion Sensor"
  sensor_name_south: "South Motion Sensor"
  sensor_name_east: "East Motion Sensor"
  sensor_name_west: "West Motion Sensor"
  fallback_ssid: "My-Fallback-AP"
  fallback_password: "AnotherPassword"
```

### Example Setup
```yaml
esphome:
  name: ${device_name}

packages:
  motion_sensor:
    url: https://github.com/DBR-it/Motion-sensors
    ref: main
    files:
      - motion_sensor.yaml

substitutions:
  device_name: "my_custom_motion_sensor"
  sensor_name_north: "North Motion Sensor"
  sensor_name_south: "South Motion Sensor"
  sensor_name_east: "East Motion Sensor"
  sensor_name_west: "West Motion Sensor"
  fallback_ssid: "My-Fallback-AP"
  fallback_password: "AnotherPassword"
```

## What This Sensor Does
- Uses an **ESP8266** (e.g., D1 Mini) with **RCWL-0516 motion sensors**.
- Detects motion through **GPIO binary sensors**.
- Provides a **web server** on port 80 for local access.
- Supports **OTA updates** for easy firmware management.
- Creates a **fallback hotspot** if Wi-Fi fails.

This approach keeps your local configuration clean and allows automatic updates through the remote package. Feel free to expand on this README or add project-specific details as needed!


