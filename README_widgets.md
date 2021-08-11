# Widgets

This manual contains examples and documentation on all different widgets and how to use them.

## Power plug / Switch

The power plug can be used, as is. If your plug supports power monitoring and other sensors you can add a `graph_entities` list of entities to show in a graph. This is 'under-the-hood' an embedded [mini-graph-card](https://github.com/kalkih/mini-graph-card) in a [button-card](https://github.com/custom-cards/button-card).

```yaml
- type: 'power_plug'
  name: 'Power plug'
  entity: 'switch.xxxxxx'
  graph_entities:
    - entity: 'sensor.xxxxx'
      show_state: true
      show_graph: true
    - entity: 'sensor.xxxxx'
      show_graph: true
```