# Class: tform_actions

Provides action logic for tform-based forms in ISPConfig, handling page load, submission, CRUD events, and plugin execution.

**Source File:** interface/lib/classes/tform_actions.inc.php

## Properties
- **id**: The primary record identifier from request parameters.
- **activeTab**: Currently active form tab.
- **dataRecord**: Associative array of submitted or loaded form data.
- **oldDataRecord**: Previous record state for updates when `db_history` is enabled.
- **plugins**: Loaded plugin instances keyed by plugin name.

## Methods
- **onLoad()**
  - Initializes templates, loads form definitions, and dispatches to `onSubmit` or `onShow`.
- **onSubmit()**
  - Processes form submission, checks client lock status, and calls `onInsert` or `onUpdate`.
- **onBeforeInsert()**, **onInsert()**, **onInsertSave($sql)**, **onAfterInsert()**
  - Hooks executed in sequence when inserting a new record; `onInsertSave` performs the database write.
- **onBeforeUpdate()**, **onUpdate()**, **onUpdateSave($sql)**, **onAfterUpdate()**
  - Hooks executed in sequence when updating a record; `onUpdateSave` performs the database write.
- **onAfterDatalogSave($insert = false)**
  - Called after datalog operations; `$insert` is true for inserts.
- **onError()**
  - Triggered on insert or update failure; used to append error messages.
- **onBeforeDelete()**, **onDelete()**, **onAfterDelete()**
  - Hooks executed when deleting a record.
- **onPrintForm()**
  - Generates a printable version of the form (disabled by default).
- **onMailSendForm()**
  - Sends the form content via email (disabled by default).
- **onShow()**
  - Renders the form view, manages navigation and messages, and calls `onShowEnd`.
- **onShowNew()**
  - Prepares and displays the form for new record creation.
- **onShowEdit()**
  - Loads and displays existing record data for editing.
- **onShowEnd()**
  - Finalizes template parsing and outputs the form.
- **loadPlugins($next_tab)**
  - Loads and initializes plugins configured for the specified tab.

## Usage
Used by tform controllers and the ISPConfig framework to execute custom logic around form CRUD operations, template rendering, and plugin integration.
