---

sidebar_position: 20
title: Events
---
 
# Events

Trivule provides the ability to listen for different JavaScript events to trigger form validation without writing additional JavaScript code. This increases flexibility and simplifies form validation management.

## Triggering Validation with Default Events

By default, Trivule uses the `blur`, and `change` events to trigger form field validation. This means that whenever a user enters, leaves, or modifies a value in a form field, validation is automatically triggered.

For instance, if you want to trigger validation when an element is hovered over by the mouse cursor, you can use Trivule's `data-tr-events` attribute and specify the `mouseenter` event as follows:

```html
<input data-tr-events="mouseenter" />
```

The `data-tr-events` attribute can also accept a list of events separated by the `|` (pipe) symbol. For example, if you want to trigger validation on the `mouseenter`, `blur`, and `my-custom-event` events, you can use the following syntax:

```html
<input data-tr-events="mouseenter|blur|my-custom-event" />
```

## Trivule Events to Listen For

Trivule also provides specific events you can listen for to respond to specific actions related to form validation. Here are some of these events:

### Input-Related Events

- `tr.input.passes`: This event is triggered when an input field passes validation successfully.
- `tr.input.fails`: This event is triggered when an input field fails validation.

### Form-Related Events

- `tr.form.init`: This event is triggered when the form is initialized and ready for validation.
- `tr.form.passes`: This event is triggered when all fields in the form pass validation successfully.
- `tr.form.fails`: This event is triggered when at least one field in the form fails validation.
- `tr.form.update`: This event is used to indicate to Trivule to update the validation with DOM changes and new rules. This can be useful when you dynamically modify form elements or add new validation rules.

## Triggering Trivule Events

In addition to listening for events, you can also manually trigger certain Trivule events to perform specific actions. Here's an important event to know:

- `tr.form.update`: This event should be triggered when you want to instruct Trivule to update validation according to DOM changes or newly added rules.

By using these events and either listening for or triggering them at the right time, you can customize the behavior of form validation with Trivule.