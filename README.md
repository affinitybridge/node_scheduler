node_scheduler
==============

A simple API to schedule operations on nodes to be run via cron.

This module allows other modules to schedule actions, and provides a hook to implement those actions when they fire.

Public function: node_scheduler_schedule_action($nid, $key, $time) schedules an action to be run in the future.

Public function: node_scheduler_remove_action($nid, $key, $time) removes an action scheduled to be run in the future.

Hook: hook_node_scheduler_action($nid, $key) allows other modules to run operations on the action.

    /**
     * Implements hook_node_scheduler_action().
     */
    function example_node_scheduler_action($nid, $key) {
      switch ($op) {
        case 'example_email_reminder':
          // TODO: Load the node from the node
          // TODO: Call drupal_mail
          break;
        case 'example_node_update':
          // TODO: Load the node from the nid
          // TODO: Make modifications to the $node object
          // TODO: Call node_save()
          break;
      }
    }
