# Code Style Guide for Nolu

## Filenames

General naming convention for filenames is snake_case with type suffixed with a dot (before the extension):

```yaml
# OK:
a_generic_example_file.yaml
nolu/custom/includes/automations/my_bathroom_ventilation.automation.yaml
nolu/custom/includes/notifiers/my_custom_notification.notify.yaml

# NOK:
a-generic-file_name.yaml
nolu/custom/includes/automations/my_bathroom_ventilation.yaml
nolu/custom/includes/notifiers/my_custom_notification.yaml
```

Take not that the directories are plural and the filename type suffix is singlar! In above example the parent folder is named `xxxx/automations/` (plural) and the suffix of the filename is `.automation.yaml` (singlar).

### Lovelace_gen files (exception to the rule)

As you might work on the code, you'll stumble upon files that are suffixed with `xxx.llg.yaml`. This suffix is created for a few different reasons:
1. For a developer its cleary visible this is a `lovelace_gen` file
2. In VScode it is easy to activate the `Better Jinja`-extensions only for these kind of files and ignore the normal yaml files.
3. It will remind the developer to make sure that these files start with the `# lovelace_gen`-comment.

### When using native HASS code

When configuring a native integration please make sure you add the manual link to the native integration or whatever to the top of the comment.

```yaml
# nolu/custom/includes/sensors/integration_sensors/dsmr.integration.yaml
####################################################################
#
#         DSMR
#
####################################################################
# https://www.home-assistant.io/integrations/dsmr/
- platform: dsmr
  host: xxx.xxx.xxx.xxx
  port: 666
  dsmr_version: 69

# nolu/custom/packages/switches.package.yaml
####################################################################
#
#         SWITCH
#
####################################################################
# https://www.home-assistant.io/integrations/switch.template/
switch:
  ...
```

## Packages folder

Obviously this folder contains all package files. In every package file you can place your custom inputs, switches and other types. It is up to you how you give structure to these files. As a rule of thumb you should consider using an include when your `.package.yaml`-file gets longer than 100 lines!

### Include statements

When using `!include`-statements make sure to place them in the appropriate `nolu/custom/includes/xxx` folder. If you, for example, want to separate your input booleans do so by creating a directory `nolu/custom/includes/input_booleans`. All files inside this directory will be suffixed with `xxxxx.input_boolean.yaml`.

### Exception for Sensors

Since sensors are handled a bit differently, because `template sensors` and `integration sensors` are created differently in HASS than `binary sensors`. The differences:

```yaml
# Template Sensor
sensor:
  - platform: template
    sensors:
      # all sensor definitions go here

# Integration Sensors
sensor: 
  - platform: integration name
    # all options for the integration

# Binary Sensors
binary_sensor:
  - platform: template
    sensors:
      # all sensor definitions go here
```

Above example show you why we separated the `sensors.package.yaml` and `sensors_binary.package.yaml`. The `template sensors` and `integration sensors` can be put in the same folder and included with `!include_dir_merge_list`. However the `binary_sensor` has a different key and will not work in that way. So take not that when a different key is needed for those kind of sensors, you should also separate them in another file `sensors_xxxxx.package.yaml`.

