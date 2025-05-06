# Class: plugin_base

Base class for all plugin classes in ISPConfig. Provides hooks for plugin lifecycle events and option management.

## Methods

- **onLoad()**
  - Called when the plugin is loaded.
- **onShow()**
  - Called to display plugin output.
- **onInsert()**
  - Called when a new record is inserted.
- **onUpdate()**
  - Called when a record is updated.
- **onDelete()**
  - Called when a record is deleted.
- **setOptions($plugin_name, $options)**
  - Sets plugin options and name.

## Properties

- **plugin_name**: Name of the plugin.
- **options**: Plugin options array.
- **form**: Reference to the form object.
