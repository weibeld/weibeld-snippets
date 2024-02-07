---
created: 2024-02-07T23:42:50UTC
edited: 2024-02-07T23:42:50UTC
title: "Extract all URLs matching a specific pattern from a website"
---

Execute the following in the JavaScript console of a web browser (e.g. Chrome):

```javascript
var urls = document.getElementsByTagName('a');
for (i in urls) {
    var href = urls[i].href
    if (href.match(/.*/)) console.log(href)
}
```
