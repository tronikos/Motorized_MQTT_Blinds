# Motorized_MQTT_Blinds

This repository is to accompany my Motorized_MQTT_Blinds video:

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/1O_1gUFumQM/0.jpg)](https://www.youtube.com/watch?v=1O_1gUFumQM)

## Parts List
Stepper Motors: https://amzn.to/2D5rVsF

Stepper Drivers: https://amzn.to/2OZqW1W (You can use A4988 or DRV8825 or TMC2208 with the TMC2208 being the quietest one)

NodeMCU: https://amzn.to/2I89xDF

12V Power Supply: https://amzn.to/2G2ZJrf

Buck Converter: https://amzn.to/2UsQ7jA

## 3D Printing

Download the correct STL file for your style of tilt rod

## Wiring Schematic

![alt text](https://github.com/thehookup/Motorized_MQTT_Blinds/blob/master/Schematic.jpg?raw=true)

**Dont forget to cut the center trace on the stepper motor as shown in the youtube video**

## Software installation

You have 3 options (from easier to harder): ESPHome, Tasmota, or Arduino IDE.

### ESPHome

See https://github.com/tronikos/esphome-blinds

### Tasmota

Use [Tasmota](https://github.com/tasmota/tasmotizer) configured in [Cover mode](https://tasmota.github.io/docs/Blinds-and-Shutters/#using-stepper-motors).

### Arduino IDE

#### File setup

Fill out the entire USER CONFIGURATION section of the code.

You should leave "STEPS_TO_CLOSE" at 12 to start with.  It can be adjusted for your specific blinds

#### Home Assistant YAML

Replace "BlindsMCU" with your MQTT_CLIENT_ID if you changed it in the file setup

Home Assistant 2022.7.5 and Later:
```yaml
mqtt:
  cover:
    - name: "BlindsKitchen"
      command_topic: "BlindsMCU/blindsCommand"
      position_topic: "BlindsMCU/positionState"
      set_position_topic: "BlindsMCU/positionCommand"
      retain: true
      payload_open: "OPEN"
      payload_close: "CLOSE"
      payload_stop: "STOP"
      position_open: 0
      position_closed: 12
```

Home Assistant 2022.6.5 and Earlier:

```yaml
cover:
  - platform: mqtt
    name: "Motorized Blinds"
    command_topic: "BlindsMCU/blindsCommand"
    set_position_topic: "BlindsMCU/positionCommand"
    position_topic: "BlindsMCU/positionState"
    retain: true
    payload_open: "OPEN"
    payload_close: "CLOSE"
    payload_stop: "STOP"
    position_open: 0
    position_closed: 12
  ```
  
## Optional - PCB Design for 3 blind system

Project File: 

GERBER FILE:Sender Board: https://github.com/thehookup/Motorized_MQTT_Blinds/blob/master/THU_Sender_Board.zip

GERBER FILE:Receiver Board: https://github.com/thehookup/Motorized_MQTT_Blinds/blob/master/THU_Receiver_Board.zip

## User Submitted PCBs

GERBER FILE: Dave Morris Quad Blind: https://github.com/thehookup/Motorized_MQTT_Blinds/blob/master/Dave_Morris_4_Blind_With_Power.zip

GERBER FILE:Joshua Garrison Single Blind: https://github.com/thehookup/Motorized_MQTT_Blinds/blob/master/Joshua_Garrison_Single_Blind.zip
  
## Recommended Tools

Ender3 3d Printer: https://amzn.to/2GcznnZ

Dupont Crimper and Connector Set: https://amzn.to/2X1Oeap

## Alexa only support available in the releases tab of this repo!
