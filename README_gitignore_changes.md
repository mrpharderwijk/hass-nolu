# Ignore changes in existing files

For a lot of files in the custom directory changes should be ignored, but the files should exist in the git repo. Git has a command to achieve this:

```
git update-index --skip-worktree FILENAME
```

To undo the above command:
```
git update-index --no-skip-worktree FILENAME
```

The list of files that should be need to be 'skipped' are:
```
# Config main
nolu/custom/custom.config.yaml
nolu/custom/customize.config.yaml

# Config sub
nolu/custom/includes/config/groups/entity_counters.group.yaml
nolu/custom/includes/config/tts/google_translate.tts.yaml
nolu/custom/includes/config/http.config.yaml
nolu/custom/includes/config/recorder.config.yaml

# Sensors
nolu/custom/includes/sensors/binary_sensors/motion_sensors.binary.yaml
nolu/custom/includes/sensors/bundled_sensors/template_sensors/entity_counters.sensor.yaml

# Packages
nolu/custom/packages/configuration.package.yaml
nolu/custom/packages/input_booleans.package.yaml
nolu/custom/packages/light_groups.package.yaml
nolu/custom/packages/persons.package.yaml
nolu/custom/packages/scenes.package.yaml
nolu/custom/packages/scripts.package.yaml
```