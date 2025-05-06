# Class: message

Provides system and user message management in ISPConfig, including adding, hiding, deleting, and retrieving dashboard notifications.

**Source File:** interface/lib/classes/message.inc.php

## Methods

- **add($message, $message_state = 'info', $sys_userid = 0, $sys_groupid = 0, $relation = '')**
  - Inserts a new message into `sys_message` with state (`info`, `warning`, `error`), optional user/group context, and relation tag.
- **hide_by_id($message_id)**
  - Marks a message as acknowledged by its ID (sets `message_ack = 'y'`).
- **hide_by_message_state($message_state, $relation = '')**
  - Acknowledges all messages of a given state and optional relation tag, respecting permission rules.
- **hide_by_message_relation($relation)**
  - Acknowledges all messages matching the specified relation tag.
- **delete($message_id)**
  - Permanently deletes a message record by ID.
- **cleanup()**
  - Removes acknowledged messages older than one month.
- **get_current_messages($relation = '')**
  - Retrieves all unacknowledged messages for the current user, optionally filtered by relation, translating via dashboard language files.

## Usage

Used by the ISPConfig dashboard to display and manage system messages requiring user acknowledgment.
