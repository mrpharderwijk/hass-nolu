# NOLU

Nolu is a Home Assistant framework that aims to make a clean-looking and
easy-to-use dashboard. The theme is a mixture between IOS, MacOS and parts picked up from the Home Assistant Community.

- [NOLU](#nolu)
  - [Prerequisites](#prerequisites)
  - [Installation instructions](#installation-instructions)
  - [The Nolu concept](#the-nolu-concept)
    - [The `custom` directory](#the-custom-directory)
      - [Creating a custom dashboard](#creating-a-custom-dashboard)
      - [Badge Counters](#badge-counters)
    - [The `core` directory](#the-core-directory)
  - [FAQ](#faq)
  - [Specials thanks, shoutouts and credits](#specials-thanks-shoutouts-and-credits)
      - [VSCode](#vscode)

## Prerequisites

For Nolu to work properly and the install process to run smoothly it is important that you have the following stuff up and running:

1. Home Assistant in `Advanced Mode`
2. The following add-on's are installed through the add-on Store:
   - [Samba Share](https://github.com/home-assistant/addons/blob/master/samba/DOCS.md)
   - [SSH & Web Terminal (Home Assistant Community Add-on)](https://github.com/hassio-addons/addon-ssh)
   - [Visual Studio Code](https://github.com/hassio-addons/addon-vscode) or [File Explorer](https://github.com/home-assistant/addons/tree/master/configurator)
   - [HACS](https://hacs.xyz/docs/installation/installation/)
3. Next up, you need to install the following HACS integrations:
   - [browser_mod](https://github.com/thomasloven/hass-browser_mod)
   - [lovelace_gen](https://github.com/thomasloven/hass-lovelace_gen)
4. After this its time to install the HACS Frontend repositories:
   - [button-card](https://github.com/custom-cards/button-card)
   - [hui-element](https://github.com/thomasloven/lovelace-hui-element)
   - [kiosk mode](https://github.com/maykar/kiosk-mode)
   - [layout-card](https://github.com/thomasloven/lovelace-layout-card)
   - [light entity card](https://github.com/ljmerza/light-entity-card)
   - [mini-graph-card](https://github.com/kalkih/mini-graph-card)
   - [mini-media-player](https://github.com/kalkih/mini-media-player)
   - [simple weather card](https://github.com/kalkih/simple-weather-card)
   - [card-mod](https://github.com/thomasloven/lovelace-card-mod)
5. Now may be a good time to do a restart of your HASS
6. When all is booted up, check `configuration` > `Lovelace Dashboards` > `Resources (tab)` and make sure all HACS Frontend resources are present

### VSCode

With great power comes great responsibility. To control all that power and the codebase I advice you to install the VSCode add-on. Go to Supervisor > Add-on Store > and search for VS Code.

Recommended extensions to use:

- [EditorConfig](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)
- [Better Jinja](https://marketplace.visualstudio.com/items?itemName=samuelcolvin.jinjahtml) by Samuel Colvin
- [Material Icon Theme](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme) by PKief

## Installation instructions

1. Now download Nolu's source from Github or clone the Nolu repository locally
2. Find the `nolu`-directory insided Nolu's source and copy it to the root of the `config`-directory of your Hass server
3.  From Nolu's source copy the contents of `configuration_example.yaml` and paste it in your own `configuration.yaml` (or use the parts you need if you know what you're doing). The `# Nolu - mandatory` rules are the ones that really need to be part of the `homeassistant:` definition, otherwise `Nolu` will not be able to start properly.
4. If you aren't using a `secrets.yaml` yet, know is the time to start using one! Rename the `secrets.sample.yaml` to `secrets.yaml` and add your privacy sensitive variables. Most of these variables are not used for the core part of `Nolu`, only the `hass_` variables are.
5. Open the custom config located at `nolu/custom_example/custom.config.yaml` and use this file to build your dashboard (for more information over what is possible check below 'Creating a custom dashboard')

???? You survived the most difficult part ????!

!IMPORTANT NOTE!
As you might have noticed we have suffixed the default nolu custom parts with `_example`. The example-parts are:

- `configuration_example.yaml` - contains the basic configuration
- `nolu/custom_example/` - this folder contains the basic custom files

You might want to proceed renaming the `configuration_example.yaml` to `configuration.yaml` and the `nolu/custom_example/`-folder to `nolu/custom/`. Don't forget to update the references to `nolu/custom_example/`-folder. By default there is a reference in the `configuration_example.yaml`.

## The Nolu concept

In the `configuration.yaml` you will see that I've split the framework in two parts. The `core`-part and the `custom`-part. The `core`-part should not be edited, as it may have consequences that are irreversible for the proper working of the theme. The `custom`-part however is free for the user to edit and play around with. I've left a basic custom directory structure intact for reference.

### The `custom` directory

By default this is called `custom_example`. We assume you renamed it to `nolu/custom/` after the installation. At the root of the `custom`-directory (`nolu/custom`) you will find the `custom.config.yaml`. This file basically contains your views definition. So this file contains the different 'pages' for your setup. Under every page you can define your entities and some extra options that are made available. More on that later (TBD).

`custom/package` - contains files that are read by the root `configuration.yaml` for the custom package. Define automations, configuration, input booleans, light groups, persons sensors etc. here.

`custom/includes` - the includes folder contains all directories/files that are in anyway included by `package` or other files. I've use the following structure:

- `includes/automations` - contains all automations (seperate directories)
- `includes/config` - contains all setup files used for integrations and others inside the `configuration.yaml`
- `includes/sensors` - contains sub directory `integration_sensors` and `template_sensors` which hold the those specific sensors
- `includes/templats` - usefull or repeately used jinja templates

#### Creating a custom dashboard

Open `nolu/custom_example/custom.config.yaml`. Creating a view is very simple. This can be done by typing in the lowercase name. The name cannot contain any spaces, use an underscore instead. Below contains more information and a typical example of a configuration.

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

Badge counters are a combination between custom grouped entities and custom entity sensors. The definition of the custom grouped entities can be found in `nolu/custom_example/includes/config/groups/entity_counters.group.yaml`. Besides the custom grouped entities Nolu uses custom entity sensors that calculate the amount of active entities. The definition of the custom entity sensors can be found in `nolu/custom_example/includes/sensors/template_sensors/sensors/entity_counters.sensor.yaml`.

The `entity_counters.group.yaml` contains a few predefined groups. A group starts with the name of the group (e.g. `all_climate_entities`). The group name is always followed by the `entities`-list in this list you define the entities that are part of that group.

### The `core` directory

[To be defined (TODO:)]

## FAQ

- Q: HACS is disabled due to ratelimited error
  - A: You can try and open the `.storage` -directory of your Hass server and remove the `HACS`-folder. This worked for us. If that doesn't help you could [check](https://community.home-assistant.io/t/github-rate-limit-error-hacs/229709) or it might mean you'll have to wait an hour for the limit to pass ???? (see [this post](https://hacs.xyz/docs/faq/initial_startup/] for more info) for more info)
- Q:  `Check Configuration` results in errors referring to browser_mod or lovelace_gen not found
  - A: Open `configuration.yaml` in your file editor and comment out the `packages` and `customize` parts of the configuration (so also the indented lines underneath them until, but not included, the `default_config:` line)

## Specials thanks, shoutouts and credits

I want to thank two people for inspiring me to create this theme/framework and without their awesome projects this wouldn't be possible.

- [Mattias Persson](https://community.home-assistant.io/u/Mattias_Persson) and his [take on designing a Lovelace UI](https://community.home-assistant.io/t/a-different-take-on-designing-a-lovelace-ui/162594).
- [Jimz011](https://community.home-assistant.io/u/jimz011) and his awesome work on creating the [Homekit Infused project](https://github.com/jimz011/homekit-infused).
