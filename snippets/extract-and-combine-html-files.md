---
created: 2024-02-07T23:42:50UTC
edited: 2024-02-07T23:42:50UTC
title: "Extract elements from multiple HTML files and concatenate them in single HTML file"
---

The following code extracts a specific element from a set of local HTML files and concatenates these element in a single output HTML file:

```javascript
const fs = require('fs');
const { JSDOM } = require('jsdom');

const extracts = []

const files = fs.readdirSync('.');
files.forEach(file => {
    if (file.endsWith('.htm')) { 
        const data = fs.readFileSync(file, 'utf8');
        const dom = new JSDOM(data);
        const document = dom.window.document;
        extracts.push(document.querySelectorAll('td > div > table')[1].outerHTML)
    }
});

const extractsJoined = extracts.join('\n')
console.log(`
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wolfgang Hadamitzky Sprachlexikon</title>
</head>
<body>
  ${extractsJoined}
</body>
</html>
`)

```
