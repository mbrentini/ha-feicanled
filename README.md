# ha-feicanled
[![hacs_badge](https://img.shields.io/badge/HACS-Custom-41BDF5.svg)](https://github.com/mbrentini/ha-feicanled)

Very sketchy right now. WIP.

Home Assistant integration for BLE based Feican LED lights such as https://www.aliexpress.com/item/1005001737650768.html
Usually these RGB Bluetooth lights are controlled via the "LED LAMP" app. 

## Installation

Note: Restart is always required after installation.

### [HACS](https://hacs.xyz/) (recommended)
Installation can be done through [HACS custom repository](https://hacs.xyz/docs/faq/custom_repositories).

### Manual installation
You can manually clone this repository inside `config/custom_components/feicanled`.

For  example, from Terminal plugin:
```
cd /config/custom_components
git clone https://github.com/sysofwan/ha-feicanled feicanled
```

## Setup
After installation, you should find Feican LED under the Configuration -> Integrations -> Add integration.

The setup step includes discovery which will list out all Feican LED lights discovered. The setup will validate connection by toggling the selected light. Make sure your light is in-sight to validate this.

The setup needs to be repeated for each light.

## Features
1. Discovery: Automatically discover Feican LED based lights without manually hunting for Bluetooth MAC address
2. On/Off/RGB/Brightness support
4. Emulated RGB brightness: Supports adjusting brightness of RGB lights
5. Multiple light support

## Not supported
[Light modes](blinking, fading, etc) is not yet supported.

## Known issues
1. Light connection may fail a few times after Home Assistant reboot. The integration will usually reconnect and the issue will resolve itself.
2. After toggling lights, Home Assistant may not reflect state changes for up to 30 seconds. This is due to a lag in Feican LED status API.

## Debugging
Add the following to `configuration.yml` to show debugging logs. Please make sure to include debug logs when filing an issue.

See [logger intergration docs](https://www.home-assistant.io/integrations/logger/) for more information to configure logging.

```yml
logger:
  default: warn
  logs:
    custom_components.feicanled: debug
```

## Credits
sysofwan for his Triones integration that served as a basis for this one https://github.com/sysofwan/ha-triones/issues 
