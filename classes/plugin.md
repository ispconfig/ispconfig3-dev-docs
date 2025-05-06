# Class: plugin

Handles the plugin system in the ISPConfig interface, including loading plugins, managing event subscriptions, and debugging plugin execution.

## Properties
- **subscribed_events**: Array of events the plugin is subscribed to.
- **debug**: Boolean flag to enable or disable debug output for plugin operations.

## Methods
- **loadPluginCache()** (private)
  - Loads available plugins from the plugins directory and updates the plugin cache in the session.

## Usage
This class is used by ISPConfig to dynamically load and manage plugins, allowing for modular extension of core functionality via event-driven mechanisms.
