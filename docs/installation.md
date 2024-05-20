---
sidebar_position: 2
title: Installation
---

# Installation

## Download or Use CDN

To use Trivule in your project, follow these steps:

1. **[Download](https://cdn.jsdelivr.net/npm/trivule@latest/dist/index.umd.js)** the Trivule library from [here](https://cdn.jsdelivr.net/npm/trivule@latest/dist/index.umd.js). Alternatively, you can use the CDN link directly: `https://cdn.jsdelivr.net/npm/trivule@latest/dist/index.umd.js`.
2. Include the Trivule library in your web page as you would any other JavaScript file.

## Installation via npm

1. Navigate to your project directory and run the following command:

```bash
npm i trivule
```

Once installed, you can use Trivule in your project as needed:

- For validating a single form field:

```js
import { TrivuleInput } from 'trivule';
const trInput = new TrivuleInput('selector'); 
```

- For validating an entire form:

```js
import { TrivuleForm } from 'trivule';
const trForm = new TrivuleForm('selector'); 
```

- For validating all forms in your project, suitable for classic HTML/CSS projects (vanilla), but also supports declarative validation:

```js
import { Trivule } from 'trivule';
const tr = new Trivule();
tr.init();
```

## Example
Here's an example of validation that doesn't require JavaScript:

```html
<form id="myForm">
    <div>
        <label class="label">Phone</label>
        <input type="text" data-tr-rules="required|phone:FR" name="phone" />
        <div data-tr-feedback="phone"></div>
    </div>
    <div>
        <label class="label">Date</label>
        <input
            type="date"
            data-tr-rules="required|date|after:now"
            name="date"
        />
        <div data-tr-feedback="date"></div>
    </div>
    <div>
        <label class="label">File</label>
        <input
            type="file"
            data-tr-rules="required|file|maxFileSize:1MB"
            name="file"
        />
        <div data-tr-feedback="file"></div>
    </div>
    <p><button type="submit" data-tr-submit>Submit</button></p>
</form>

<script src="https://cdn.jsdelivr.net/npm/trivule@latest/dist/index.umd.js"></script>
<script>
const tr = new Trivule();
tr.init();
</script>
```