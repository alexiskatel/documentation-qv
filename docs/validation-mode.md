---
sidebar_position: 3
title: Validation modes 
---
 
**Trivule** offers two main modes of validation: declarative validation and imperative validation.

## Declarative Validation
Declarative validation allows you to use HTML attributes to validate a form without writing any JavaScript code. This approach is intuitive and particularly suitable for simple projects that do not require conditional validation.

Trivule uses HTML attributes to configure and customize form validation. These attributes, all of which start with `data-tr`, provide a simple and intuitive approach to defining validation rules, events, error messages, CSS classes, and other features related to form field validation. Here are the most commonly used Trivule attributes:

1. **`data-tr-rules`**:
   - **Purpose**: Define the validation rules for a form field.
   - **Example**: `<input type="text" data-tr-rules="required|email">`

2. **`data-tr-events`**:
   - **Purpose**: Specify the trigger events for form field validation.
   - **Example**: `<input type="text" data-tr-events="blur|input">`

3. **`data-tr-messages`**:
   - **Purpose**: Define custom error messages for a form field.
   - **Example**: `<input type="text" data-tr-rules="required" data-tr-messages="This field is required.">`

4. **`data-tr-invalid-class` and `data-tr-valid-class`**:
   - **Purpose**: Define CSS classes to apply to a form field based on its validation state.
   - **Example**: `<input type="text" data-tr-invalid-class="invalid" data-tr-valid-class="valid">`

5. **`data-tr-auto`**:
   - **Purpose**: Enable or disable automatic validation during input.
   - **Example**: `<input type="text" data-tr-auto="true">`

6. **`data-tr-feedback`**:
   - **Purpose**: Specify a feedback element associated with a form field.
   - **Example**: `<span data-tr-feedback class="feedback-icon"></span>`

7. **`data-tr-submit`, `data-tr-enabled-class`, and `data-tr-disabled-class`**:
   - **Purpose**: Configure the form submission button in relation to validation and apply corresponding CSS styles.
   - **Example**: `<button type="submit" data-tr-submit data-tr-enabled-class="enabled" data-tr-disabled-class="disabled">Submit</button>`

8. **`data-tr-name`**:
   - **Purpose**: Change the field's name in the error message.
   - **Example**: `<input type="text" data-tr-name="our conditions">`

9. **`data-tr-lang`**:
   - **Purpose**: Specify the language used for error messages and Trivule's user interface elements.
   - **Example**: `<form data-tr-lang="fr">...</form>`

## Imperative Validation
Imperative validation provides advanced validation capabilities, allowing for conditional operations and modifications in real-time based on user interactions. This approach is ideal for forms where validation rules may change dynamically.

```javascript
const trivuleForm = new TrivuleForm("form", {
  feedbackSelector: ".invalid-feedback",
  realTime: true,
});

trivuleForm.make({
  email: {
    rules: ["required", "email", "maxlength:60"],
    feedbackElement: ".invalid-feedback",
  },
});

trivuleForm
  .get("email")
  .appendRule({
    rule: "endWith:@gmail.com",
  })
  .removeRule("maxlength");
```

#### Advanced Operations
Whether you choose declarative or imperative mode, the validation instance you create remains available for performing advanced operations such as:
- Changing rules
- Adding rules
- Removing rules
- Styling
- Interacting with events, etc.

 