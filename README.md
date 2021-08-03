# NOLU

Nolu is a Home Assistant framework that aims to make a clean-looking and
easy-to-use dashboard. The theme is a mixture between IOS, MacOS and parts picked up from the Home Assistant Community.

## Prerequisites

### Add-ons

#### HACS

This theme heavily relies on HACS. It uses several add-ons and repositories that can only be installed
using HACS. If you haven't installed HACS yet, do it now by [clicking here](https://hacs.xyz/docs/installation/installation/).

#### VSCode

With great power comes great responsibility. To control all that power and the codebase I advice you to install the VSCode add-on. Go to Supervisor > Add-on Store > and search for VS Code.

Recommended extensions to use:

- [EditorConfig](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)
- [Better Jinja](https://marketplace.visualstudio.com/items?itemName=samuelcolvin.jinjahtml) by Samuel Colvin
- [Material Icon Theme](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme) by PKief

## Integrations (A-Z)

- [button-card](https://github.com/custom-cards/button-card)
- [browser_mod](https://github.com/thomasloven/hass-browser_mod)
- [hui-element](https://github.com/thomasloven/lovelace-hui-element)
- [kiosk mode](https://github.com/maykar/kiosk-mode)
- [layout-card](https://github.com/thomasloven/lovelace-layout-card)
- [light entity card](https://github.com/ljmerza/light-entity-card)
- [light popup card](https://github.com/DBuit/light-popup-card)
- [lovelace_gen](https://github.com/thomasloven/hass-lovelace_gen)
- [mini-graph-card](https://github.com/kalkih/mini-graph-card)
- [mini-media-player](https://github.com/kalkih/mini-media-player)
- [simple weather card](https://github.com/kalkih/simple-weather-card)

## Installation

1. Download the latest stable version from releases page.
2. Unpack the zip and place the `nolu`-directory in your Home Assistant `config`-folder.
3. From the unpacked source copy/paste the `configuration.yaml` and replace your own (or use the parts you need if you know what you're doing). The `# Nolu - mandatory` rules are the ones that really need to be part of the `homeassistant:` definition, otherwise `Nolu` will not be able to start properly.
4. If you aren't using a `secrets.yaml` yet, know is the time to start using one! Rename the `secrets.sample.yaml` to `secrets.yaml` and add your privacy sensitive variables. Most of these variables are not used for the core part of `Nolu`, only the `hass_` variables are.
5. Open the custom config located at `nolu/custom/custom.config.yaml` and use this file to build your dashboard (for more information over what is possible check below 'Creating a custom dashboard')

## The Nolu concept

In the `configuration.yaml` you will see that I've split the framework in two parts. The `core`-part and the `custom`-part. The `core`-part should not be edited, as it may have consequences that are irreversible for the proper working of the theme. The `custom`-part however is free for the user to edit and play around with. I've left a basic custom directory structure intact for reference.

### The `custom` directory

At the root of the `custom`-directory (`nolu/custom`) you will find the `custom.config.yaml`. This file basically contains your views definition. So this file contains the different 'pages' for your setup. Under every page you can define your entities and some extra options that are made available. More on that later (TBD).

`custom/package` - contains files that are read by the root `configuration.yaml` for the custom package. Define automations, configuration, input booleans, light groups, persons sensors etc. here.

`custom/includes` - the includes folder contains all directories/files that are in anyway included by `package` or other files. I've use the following structure:

- `includes/automations` - contains all automations (seperate directories)
- `includes/config` - contains all setup files used for integrations and others inside the `configuration.yaml`
- `includes/sensors` - contains sub directory `integration_sensors` and `template_sensors` which hold the those specific sensors
- `includes/templats` - usefull or repeately used jinja templates

#### Creating a custom dashboard

Open `nolu/custom/custom.config.yaml`. Creating a view is very simple. This can be done by typing in the lowercase name. The name cannot contain any spaces, use an underscore instead. Below contains more information and a typical example of a configuration.

```yaml
# custom.config.yaml

example_home:
  name: 'Example Home'
  title: 'mdi:home-assistant'
  url: 'home'
  show_in_navbar: true
  show_header: true
  # `rows` - list that can contain multiple single rows
  rows:
    # `rows item` - a single row containing its elements (which are mostly what Home Assistant calls cards)
    - widgets:
        # To be defined (TODO:)...
```

#### Badge Counters

Badge counters are a combination between custom grouped entities and custom entity sensors. The definition of the custom grouped entities can be found in `nolu/custom/includes/config/groups/entity_counters.group.yaml`. Besides the custom grouped entities Nolu uses custom entity sensors that calculate the amount of active entities. The definition of the custom entity sensors can be found in `nolu/custom/includes/sensors/template_sensors/sensors/entity_counters.sensor.yaml`.

The `entity_counters.group.yaml` contains a few predefined groups. A group starts with the name of the group (e.g. `all_climate_entities`). The group name is always followed by the `entities`-list in this list you define the entities that are part of that group.

### The `core` directory

[To be defined (TODO:)]

## Specials thanks, shoutouts and credits

I want to thank two people for inspiring me to create this theme/framework and without their awesome projects this wouldn't be possible.

- [Mattias Persson](https://community.home-assistant.io/u/Mattias_Persson) and his [take on designing a Lovelace UI](https://community.home-assistant.io/t/a-different-take-on-designing-a-lovelace-ui/162594).
- [Jimz011](https://community.home-assistant.io/u/jimz011) and his awesome work on creating the [Homekit Infused project](https://github.com/jimz011/homekit-infused).
