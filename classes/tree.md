# Class: tree

Implements a data structure for hierarchical trees, used for representing nested categories or objects.

## Methods

- **loadFromArray($nodes)**
  - Loads a tree structure from an array of nodes.
- **update($id, $data)**
  - Updates the data for a given node ID.
- **regEvent($event, $class_name, $function_name)**
  - Registers an event handler for tree events (insert, update, delete).

## Properties
- **obj**: Array of tree nodes.
- **events**: Registered event handlers.
- **data_field**: Field name for node data (default: 'name').
- **primary_field**: Primary key field (default: 'media_cat_id').
- **parent_field**: Parent node field (default: 'parent').
- **root_id**: ID of the root node (default: '0').
- **opt_spacer**: Spacer string for indentation.
