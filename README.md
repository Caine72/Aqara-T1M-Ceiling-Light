# Aqara-T1M-Ceiling-Light
Zigbee2MQTT external converter for Aqara T1M Ceiling Light with RGB ring light segment control and dynamic RGB effects.

Installation:
In Zigbee2MQTT go to settings>>dev console>>external converters, create a new converter named t1m.mjs and paste in the contents of the file. Click save then restart Zigbee2MQTT via settings>>tools
Alternatively place the file t1m.mjs in the folder zigbee2mqtt/data/external_converters and restart Zigbee2MQTT.

If an external converter is active for a device a cyan icon with "Supported: external" will be displayed nuder the device name in Zigbee2MQTT.

Home Assistant:
aqara-t1m-ring-segments.yaml - blueprint to control the RGB ring light segments. Import the file into HA blueprints/script.
aqara_t1m_rgb_effects.yaml - card for HA buttons for activing RGB dynamic effects and creating custom effects.

Notes:
  
  • This converter mimics the dynamic RGB effect creation and preview feature of the Aqara Home app.
  
  • The dynamic RGB effects are not written as scenes to the light's memory as they are when using the Aqara app. That process is done via OTA firmware writes which are not implemented here.
  
  • Activating such saved effect scenes as well as the light's built in scenes appears to have some sort of vendor lock. Possibly the light is checking if the Zigbee commands are coming from an Aqara hub and won't activate them if the source IEEE address doesn't match.
  
• As such, every time you want to activate a particular effect you will have to send the parameters for that effect to the light again (colour selections, brightness, speed and effect type). 

• White Dynamic Effects are similarly done via OTA firmware writes, however the preview feature is also done this way with these effects.

• Further investigation needs to be done on the White Dynamic Effects and also the OTA firmware writing process to see how these can be replicated.
