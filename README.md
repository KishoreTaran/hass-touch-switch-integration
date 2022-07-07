# hass-touch-switch-integration
integrate Capacitive touch switch with Home assistant

esphome:
  name: intruder-detection

esp8266:
  board: nodemcuv2

# Enable logging
logger:

# Enable Home Assistant API
api:
  encryption:
    key: "UHV1TX+hg/vnICI38AomNrqvA+VabtFt81IkkNOzRYc="

ota:
  password: "2eae1308ff0d09a62a1212e632021229"

wifi:
  ssid: test1
  password: 789321456@#

  # Enable fallback hotspot (captive portal) in case wifi connection fails
  ap:
    ssid: "Intruder-Detection"
    password: "efcm3LyuDjgd"

captive_portal:

binary_sensor:
  - platform: gpio
    pin:
      number: GPIO5
      mode: INPUT_PULLUP
      inverted: True
    name: "front-door-sensor"
  - platform: status
    name: "Front door sensor"
  - platform: gpio
    pin:
      number: GPIO14
    name: "touch-switch1"
    
switch:
  - platform: gpio
    pin: GPIO4
    inverted: True
    name: "alarm"
    id: alarm  
