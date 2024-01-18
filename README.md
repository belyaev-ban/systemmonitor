# Home Assistant: System Monitor
This is forked version of the System Monitor integration from the Home Assistant core (v2024.1.3), originally created by @gjohansson-ST
This custom integration removes the diagnostic category from System Monitor entities, making them visible on automatic dashboards.


### This integration overrides the built-in System Monitor!


## Description
In the 2024.1 release, Home Assistant introduced the System Monitor integration to its core, enabling the easy setup of the integration through the user interface. 
However, a consequence of this update was that all System Monitor entities were automatically labeled as diagnostic. 
As a result, they failed to appear in the default dashboards, with no straightforward means to change that behaviour.


Since I've never bothered to configure a custom dashboard, I decided it would be easier to comment out the line that designates entities as diagnostic. 
This results in the entities showing up in default and automatic dashboards, as they did before the 2024.1 release.
Same behaviour as when System Monitor integration was configured through configuration.yaml.


## Installation
As per Home Assistant's [documentation](https://developers.home-assistant.io/docs/creating_integration_file_structure/#where-home-assistant-looks-for-integrations)
1. Navigate to Home Assistant [config directory](https://www.home-assistant.io/docs/configuration/#editing-configurationyaml)
2. In config directory create `custom_components` directory if it does not exist and navigate into it
   ```
   mkdir -p custom_components && cd custom_components
   ```
3. Clone this repository
    ```
    git clone https://github.com/belyaev-ban/systemmonitor.git
    ```
4. Restart Home Assistant

From this point on all enabled and visible System Monitor entities should be available on default and automatic dashboards.


## Changes made
*  `sensor.py:739` - commented out diagnostic category setting
   ```python
   # Commented out in order to enable visible and enabled sensors on automatic dashboards
   # _attr_entity_category = EntityCategory.DIAGNOSTIC
   ```
*  `manifest.json:2` - added version number ([Required for custom integrations](https://developers.home-assistant.io/docs/creating_integration_manifest#version))
   ```
   "version": "1.0.0",
   ```
* Also added `LICENCE` file as per original licence requirements and `.gitignore` and `README.md` files for convenience.

## Disclaimer
This modified System Monitor integration is a personal project and is not officially endorsed by the Home Assistant community or maintainers.
Use it at your own discretion.
While efforts have been made to ensure compatibility and functionality, there is no guarantee of ongoing support or updates.
The original System Monitor integration is part of Home Assistant, and any modifications made here are specific to personal preferences.
This project is provided as-is, and the author takes no responsibility for any issues, data loss, or other consequences that may arise from its use.
Feedback and contributions are welcome, but there is no obligation to provide support.
Feel free to contribute, report issues, or provide feedback by creating an issue or pull request.