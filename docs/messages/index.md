---
sidebar_position: 15
title: Messages
---

# Messages
Trivule comes with default messages, but it offers you the option to rewrite a message, or translate it into given languages.

Trivule does not impose where to display the error message; it offers the possibility to select where to display your message, giving you the opportunity to better design your error without having to perform calculations or injections yourself.

By default, validation messages are displayed in English on an HTML element (such as a `div`, `p`, or `span`) with the attribute `data-tr-feedback="file"`. Like with rules, you can use either the declarative or imperative mode to modify the messages.

```html
<input
    type="file"
    data-tr-rules="required|mimes:text/plain"
    data-tr-messages="Le fichier est requis|Le fichier doit être un fichier texte"
    name="file"
/>

<div data-tr-feedback="file"></div>
```
or
```js
{
	file: {
	    rules:"required|mimes:text/plain",
	    messages:"Le fichier est requis|Le fichier doit être un fichier texte",
	    feedbackElement:"[data-tr-feedback]"
    }
}
```
Trivule displays error messages at the nearest feedback element to the input. If you use a general selector, it will be the first encountered element around the input.

## Displaying the message
>When Trivule needs to display error messages, it first determines the language in which these messages should be displayed. Here's how it works:

### Via HTML

First, Trivule checks the language set on the `lang` attribute of the root `html` element:
```html
<html lang="en"></html>
```

If Trivule supports the language defined in the `lang` attribute, or if you have added your own languages, the error messages will be displayed in that language.

If, for any reason, you don't want to use the language defined in the `lang` attribute, you can use the `data-tr-lang` attribute on the root element to specify the language in which the messages should be displayed.

```html
<html data-tr-lang="en"></html>
```

The `data-tr-lang` attribute can also be used on a form element to specify the language for that specific form.
```html
<form data-tr-lang="en"></form>
```
This means that error messages will be specific to each form.

### Via JavaScript

Trivule offers another way to specify the language of error messages using JavaScript:

```javascript
TrLocal.local('es');
```
This tells Trivule to display messages in Spanish. This method overrides all other methods of language assignment for displaying error messages.

**Note:**

All language assignment methods must be used before calling the `init()` method.
This method should be called before initialization methods, constructors, or the `init()` method.

### Placeholders

Suppose you have an additional validation rule for the "Email" field: it must have a minimum length of 8 characters. You want to specify a specific error message for this rule.

You can use placeholders to indicate error messages in any order. Here's how you can do it:

```html
<input type="email" name="email" data-tr-messages="{0}Please enter a valid email address|{1}Email must be at least 8 characters long">
```

With this configuration, Trivule will display the first error message if the email address is invalid, and the second error message if the minimum length of 8 characters is not met.

## Modifying an Existing Message

If you want to modify an existing message in Trivule, you can use the `rewrite(lang, rule, message)` method. For example, if you want to customize the message for the `min` rule in English, you can do the following:

```javascript
TrLocal.rewrite('en', 'min', 'Your custom message for the min rule');
```

You can also use the `rewriteMany(lang, rules, messages)` method to modify multiple messages at once.

```javascript
TrLocal.rewriteMany('en', ['min', 'max'], ['Min rule message', 'Max rule message']);
```

It is important to provide the error messages in the respective order of the rules.

Once you have modified or added messages, Trivule will use the updated versions of the messages for the corresponding rules.


### Parameters in Messages

Sometimes, you may want to include specific information such as the field name in error messages. You can do this by using parameters in the messages. For instance, to include the field name in a message, use `:field` in the message. For example:

```markdown
The field :field is required.
```

When the error message is generated, `:field` will be replaced with the actual name of the field.

If you have multiple parameters to pass in a message, you can represent them with `:arg1`, `:arg2`, etc. For example, if you have a `min` rule with a parameter of `9MB` (`data-tr-rules="min:92"`), you can use the following message:

```markdown
The size must exceed :arg0.
```

The result would be:

```markdown
The size must exceed 9MB.
```

If you have multiple possible values for a rule, you can use `...arg` to display the list of parameters. For example, if you have an `in` rule with the parameters `active`, `inactive`, `etc.` (`data-tr-rules="in:active,inactive"`), you can use the following message:

```markdown
The field value must be one of the following: ...arg.
```

The result would be:

```markdown
The field value must be one of the following: active, inactive, etc.
```

By using these customizations for error messages, you can make Trivule validations more tailored to your specific translation and customization needs.

## Translation

By default, error messages are in English. However, you can translate these messages into your preferred language using the `TrLocal` class. Trivule natively supports two languages: French and English.

To translate messages into your language, you can use the `translate(lang, messages)` method. For example, to translate messages into Spanish, you can use the following code:

```javascript
TrLocal.translate('es', {
  min: "El campo :field debe ser menor que :arg0",
  rule1: "Mensaje 1",
  etc: "etc."
});
```

Make sure to translate all messages for each rule you use; otherwise, some messages may remain in English.