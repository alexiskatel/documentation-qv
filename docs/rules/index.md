---
sidebar_position: 5
title: Rules
---
 
# Rules 

In this section of the documentation, we'll explore the various validation rules provided by Trivule for validating fields. Each rule represents a specific condition that a field must meet to be considered valid. Here are the available validation rules:

Some rules can accept arguments while others cannot. The arguments for a rule are specified after the colon (:) in the rule's usage.

The examples provided in this documentation will be declarative to be more explicit and simple, but the usage remains the same regardless of the type of validation used.

## Strings

The `string` rule allows you to validate fields of type string. It enables you to check conditions such as minimum and maximum length, the presence of alphabetic, numeric, or special characters, and more.

### `email`

The `email` rule validates an email address.

**Usage:** Ensure that an email address entered by the user is valid.

### `minlength`

The `minlength` rule validates the minimum length of a string.

**Usage:** Ensure that a string entered by the user has a specified minimum length.

**Example:**
```html
<input data-tr-rules="minlength:8" /> 
```
or in JavaScript
```js
{
    rules:"minlength:8"
}
```

### `maxlength`

The `maxlength` rule validates the maximum length of a string.

**Usage:** Ensure that a string entered by the user has a specified maximum length.

**Example:**
```html
<input data-tr-rules="maxlength:8" /> 
```
or in JavaScript
```js
{
    rules:"maxlength:8"
}
```  

### `url`

The `url` rule validates a URL.
Ensure that a URL entered by the user is valid.

### `startWithUpper`

 Ensure that a string entered by the user starts with an uppercase letter.

### `lower`

The `lower` rule verifies if the entered data consists only of lowercase letters.
```html
<input type="text" data-tr-rules="lower" />
```
 
###  `upper`

The `upper` rule verifies if the input contains uppercase letters.

```html
<input type="text" data-tr-rules="upper" />
```

### `excludes`

This rule verifies that the input does not contain any of the characters specified in the exclusion list. The excluded characters must be separated by commas.

**Usage:**
```html
<input data-tr-rules="excludes:-,@" />
```
If you want to exclude spaces, you should use the special character `&esp;` instead of the regular space character.

**Example:**
```html
<input data-tr-rules="excludes:-,@,&esp;" />
``` 

### `stringBetween`

This rule verifies that the length of a given string falls within the specified minimum and maximum values.

**Usage:**

Use the `stringBetween` rule when you want to ensure that the length of a string is within a specific range.

**Example:**

Suppose you have a form that requires a password field, and you want to impose a minimum and maximum length for the password. You can apply the `stringBetween` rule to the password input field to validate it.

```html
<input data-tr-rules="stringBetween:8,20" />
```

This will ensure that the value entered in the field has a length between 8 and 20 characters (inclusive). If the length of the input is less than 8 or more than 20, the validation will fail.


## Numbers

These validation rules are specifically designed for numbers. They allow you to verify whether a numeric value satisfies certain conditions. Here is a detailed description of each rule and examples of practical usage:

### `min` 
The `min` rule allows you to check if a number is greater than or equal to a specified minimum value. 

**Example:**
```html
<input tr-rules="min:2"/>
```


### `max` 
The `max` rule allows you to check if a number is less than or equal to a specified maximum value.
 

**Example:**
```html
<input tr-rules="max:20"/>
``` 

### `integer` 

The `integer` rule allows you to check if a number is an integer.

**Alias:** `int`
 

**Example:**
```html
<input tr-rules="integer"/>
<!-- or -->
<input tr-rules="int"/>
```

### `number` 

The `number` rule allows you to check if a value is a number.
 

**Example:**
```html
<input tr-rules="number"/>
```

### `modulo` 

The `modulo` rule, also known as its alias `mod`, allows you to check if a number is a multiple or divisible by another number.  

**Example:**
```html
<input tr-rules="modulo:2"/>
<input tr-rules="mod:2"/>
``` 
 

### `numberBetween` 

The `numberBetween` rule allows you to check if a number falls within a specified range.
 
**Example:**
```html
<input tr-rules="numberBetween:10,20"/>
```

### `lessThan` 

The `lessThan` rule, also known by its alias `lthan`, allows you to check if a number is less than a specified value. 

**Example:**
```html
<input tr-rules="lessThan:100"/>
<!-- Alias -->
<input tr-rules="lthan:100"/>
```

### `greaterThan` 

The `greaterThan` rule, also known by its alias `gthan`, allows you to check if a number is greater than a specified value.
 

**Example:**
```html
<input tr-rules="greaterThan:0"/>
<!-- Alias -->
<input tr-rules="gthan:0"/> 
```
## Dates


The following rules are used to validate dates. These rules allow you to verify whether an input is a valid date, compare dates, and check if a date falls within a specific range.

>Note: Date format passed as an argument should be [JavaScript specification](https://tc39.es/ecma262/multipage/numbers-and-dates.html#sec-date-time-string-format). Example format: YYYYY-MM-DDTHH:mm:ss.sssZ or its variants.

### `date`

This rule checks if the input is a valid date.

**Example:**
```html
<input type="text" data-tr-rules="date" />
```

### `before`

This rule checks if the entered date is before a specified date.

**Example:**
```html
<input type="date" data-tr-rules="before:2020-11-11" />
```

### `after`

This rule checks if the entered date is after a specified date.

**Example:**
```html
<input type="date" data-tr-rules="after:now" />
```

### `dateBetween`

This rule checks if the entered date falls between two other dates.

**Example:**
```html
<input type="date" data-tr-rules="dateBetween:2020-11-11,now" />
```

### `time`

This rule checks if the entered time is in the 24-hour format.

**Example:**
```html
<input type="time" data-tr-rules="time" />
```


## Files 

### `file`

This rule checks if the input value is a `File` or `Blob` or `FileList` object.

```html
<input data-tr-rules="file" />
```
 

###  `maxFileSize`

This rule checks if the file size is less than or equal to a given maximum size.

```html
<input data-tr-rules="maxFileSize:1MB" />
``` 

### `minFileSize`

This rule checks if the file size  is greater than or equal to a given minimum size.

```html
<input data-tr-rules="minFileSize:1MB" />
```
 
### `fileBetween`

This rule checks if the file size falls between specified minimum and maximum values.

```html
<input data-tr-rules="fileBetween:1MB,5MB" />
```
 

### `mimes`

The `mimes` rule is used to verify if the file MIME type matches the specified MIME type(s). It allows you to validate file uploads based on their MIME types.

#### Usage

The `mimes` rule validates the MIME type of the uploaded file by comparing it to the specified MIME types.

#### Examples

- **Accept only PDF files:**
```html
<input type="file" data-tr-rules="mimes:.pdf">
```

- **Accept multiple MIME types:**
```html
<input type="file" data-tr-rules="mimes:image/jpeg, image/png">
```

- **Accept specific MIME type groups:**
```html
<input type="file" data-tr-rules="mimes:audio/*">
```

- **Using wildcards:**
```html
<input type="file" data-tr-rules="mimes:image/*">
```
- **Accepts all types:**
```html
<input type="file" data-tr-rules="mimes:*">
```
  

## Phone Numbers 
These rules are specifically designed for phone number validation. They allow you to verify the format of phone numbers. Here is a detailed description of each rule and practical usage examples:

> Please note that the code and examples provided may contain errors or limitations due to the complexity and variations of phone number formats across different regions and countries. It is always recommended to perform additional validation or consult relevant standards when working with phone numbers.

### `phone`

The `phone` rule validates the format of a phone number. Given the diversity of phone numbers, this validation may not cover all possible cases. 

**Example:**
```html
<input data-tr-rules="phone:FR,BJ" /> 

<input data-tr-rules="phone" /> 
```

In the first example, the rule validates the phone number based on the specified country codes (FR, BJ). It ensures that the entered phone number follows the format used in the respective countries.

In the second example, the rule validates phone numbers globally, without any restriction on specific country codes.



## Global Rules

The `global` rule encompasses general validation rules that can be used for specific cases. 

### `required`

This rule checks if the input is not empty (not null, not undefined, not empty string). If the input value is empty, the validation fails.

### Example

```html
<input data-tr-rules="required" />
``` 

---
 
### `in`
 
This rule checks if the input value is part of the specified list of values. Values must be separated by a comma.

### Example

```html
<input data-tr-rules="in:active,inactive" />
```

In this example, the `in` rule is applied to an input field. It checks if the input value is either "active" or "inactive."

 
### `size`
 
### Usage

```html
<input type="text" data-tr-rules="size:6" />
```
or

```html
<input type="file" data-tr-rules="size:6MB" />
```
### Description

This rule checks if the input adheres to the specified maximum size. The rule is applied differently depending on the type of input:

- If the input value is a file, the rule checks the maximum file size.
- If the input value is not a file, the rule checks the number of characters in the input.

### Example

```html
<input type="text" data-tr-rules="size:6" />
```

In this example, the `size` rule is applied to an input field. It checks if the size of the input is equal to 6 characters.  

 

### `boolean`

This rule checks if the input corresponds to a boolean value. The accepted values are: "`true`," "`false`", "`0`", "`1`", "`yes`, and "`no`" 

### Example

```html
<input data-tr-rules="boolean" />
```

 

### `between`

This rule allows you to validate different types of data by specifying a range of values. Possible ranges of values depend on the type of data:

- For numbers, the rule checks if the input value falls within the specified minimum and maximum values.
- For strings, the rule checks if the length of the string falls within the specified minimum and maximum lengths.
- For dates, the rule checks if the input date falls within the specified minimum and maximum dates.
- For files, the rule checks if the file size falls within the specified minimum and maximum file sizes.

### Example

```html
<!-- Valid number -->
<input type="number" data-tr-rules="number|between:6,7" />

<!-- Valid string -->
<input type="text" data-tr-rules="between:6,7" />

<!-- Valid date -->
<input type="date-local" data-tr-rules="date|between:2021-01-01,now" />

<!-- Valid file size -->
<input type="file" data-tr-rules="file|between:2MB,3MB" />
```
  

###  `regex`
This rule checks if the input value matches the specified regular expression. The regular expression is defined using standard regex syntax without the `/` characters at the beginning and end.

### Example

```html
<input data-tr-rules="regex:^[A-Z]+$" />
```

In this example, the `regex` rule is applied to an input field. It checks if the input value is a sequence of uppercase letters.

#### Note
The `regex` rule in Trivule typically uses the `|` symbol as a separator to specify multiple regular expressions. However, this can pose problems if the `|` symbol is present in your regular expression. To address this issue, Trivule offers the use of a special character '`&pip;`' as a substitute for the `|` symbol.

Instead of writing your `regex` rule like this:

```html
<input data-tr-rules="regex:^abc|def$" />
```

You can use the character '`&pip;`' in place of the `|` symbol, like this:

```html
<input data-tr-rules="regex:^abc&pip;def$" />
```

This way, Trivule will recognize that you want to use the `|` symbol in your regular expression without interpreting it as a rule separator.

Be sure to follow this convention when using the `regex` rule in Trivule to avoid any confusion or errors related to the `|` symbol.

---

### `only`

This rule allows you to validate an input based on its type. Two types are currently supported: "string" and "number." The rule checks if the input value matches the specified type.

### Example

```html
<input data-tr-rules="only:string" />
```

In this example, the `only` rule is applied to an input field. It checks if the input value is a string containing only string.


###  `digit`

The `digit` rule verifies if the input consists only of digits (0-9).
If the param passed, It will check if the digit has the provided param int size

```html
<input type="text" data-tr-rules="digit" />
or
<input type="text" data-tr-rules="digit:6" />
```
 
###  `minDigit`

The `minDigit` rule checks if the input contains a minimum number of digits.

```html
<input type="text" data-tr-rules="minDigit:3" />
```
 
###  `maxDigit`

The `maxDigit` rule checks if the input contains a maximum number of digits.

```html
<input type="text" data-tr-rules="maxDigit:10" />
```
 

###  `length` (alias: `len`)

The `length` rule validates the length of the input string.

```html
<input type="text" data-tr-rules="length:5" />
or
<input type="text" data-tr-rules="len:5" />
``` 

### `startWithString`

The `startWithString` rule verifies if the input string starts with a specified substring.

```html
<input type="text" data-tr-rules="startWithString:prefix" />
```

###  `endWithString`

The `endWithString` rule checks if the input string ends with a specified substring.

```html
<input type="text" data-tr-rules="endWithString:suffix" />
``` 

## Add or modify a new rule in Trivule?

Let's say the `required` rule doesn't meet your requirements. You want to customize its behavior or add a new rule. The `rule` method of the `TrBag` class is here for that.

Here's how to add or modify a rule in Trivule:

```javascript
TrRule.add("required", (input) => {
  return {
    value: input,
    passes: false,
  };
});
```

This method takes four parameters, two of which are required:

- **rule**: The name of the rule.
- **callback**: The callback. This callback takes three parameters, one of which is required. The first is the value of the field to validate, the second is the argument passed to the rule, and the third is the field type. Only the value is required. This callback must return an object in the following format:
```js
{
  value: value, // The value can be modified to serve the next rule.
  passes: true, // or false: indicates if the predicate passed.
  type: "text", // Optional but necessary for specific types, such as numbers, dates, etc.
  alias: "required", // Optional but useful when the rule can change depending on the data type and refer to another.
}
```
Explanation on `alias`:
When we take the `min` rule, it is a general rule that validates numbers, strings, file sizes, etc. When the data type to be validated is a `string`, the rule simply calls the `minlength` rule to avoid rewriting another logic.

- **message**: The message to display when the rule fails.
- **locale**: The language of the message if it was not in English .

### Complete Example

```typescript
const notSudoRule: RuleCallBack = (input: string) => {
  return {
    value: input,
    passes: input != "sudo",
    type: "text", // Optional
    alias: undefined, // Optional
  };
};

TrRule.rule(
  "notSudo",
  notSudoRule,
  "The input value should not be 'sudo'",
  "en"
);
```

Once this step is completed, your rule is available in Trivule, and you can use it just like you would with Trivule's other rules.