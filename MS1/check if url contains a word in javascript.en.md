+++
title = "Check if url Contains a Word in JavaScript"
date = 2021-02-04
draft = false
keywords = ["check if url contains a word in javascript"]
description = "Different methods in JavaScript to check if the URL on a website contains a word."
postlink = 34649131
inarticle = true
tags = ["JavaScript", "JavaScript URL"]
author = "Abdullahi Salawudeen"

+++

The address bar of a web browser displays the URL of a website by default. The URL may contain parameters or arguments, often dynamically defined to communicate with elements or objects on a web page. 

Sometimes, data passed to the URL as parameters could be extracted. There are different methods in `JavaScript` to check if the URL contains a defined string or value, like the `indexOf()`,  `RegExp,` and `Match()` method.

This tutorial illustrates how to use these methods to check if a URL contains a target keyword, in this case, `Desktop` would be used as the keyword.

## Use `Window.location.href.indexOf()` to check if URL contains a specific word in JavaScript

As observed from the function name, it returns the current URL on the web browser. DOM does not have to be loaded to check if a URL contains a search word. 

The `Window.location.href.indexOf()` returns the index of the keyword in the URL. The target word is output with an alert() function when the returned value is above zero (0). Further discussion is available via [this reference](https://www.w3schools.com/jsref/jsref_indexof.asp).

Below is an example code.

```html
<html>
<head>
<script type="text/javascript">
    if(window.location.href.indexOf("Desktop") > -1)     {
       alert("Alert: Desktop!");
    }
</script>
</head>
<body>
    <h2>
        Check if url contains the word Desktop
    </h2>
</body>
</html>
```

## Use `Window.location.href.indexOf()` in a custom function to check if URL contains a specific word in JavaScript


`Window.location.href.indexOf()` could be used in a custom function called `checkUrl()`. Once a button is clicked, the `onclick()` event is triggered then the `checkUrl()` function executes. 

The target word could be output on the console when the returned value is above zero (0) by calling the `console.log()` function. A further discussion on the `onclick()` event is available via [this reference](https://www.w3schools.com/jsref/event_onclick.asp).

Below is an illustration.

```html
<!DOCTYPE html>
<html>
<head>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.10.1/jquery.min.js"></script>
 </head>
<body>
    <input id="bt" type="button" onclick="checkUrl()" value="Check URL" />
</body>

<script>
    function checkUrl() {
        if (window.location.href.indexOf('Desktop') > 0) {
            console.log("The URL contains Desktop");
        }
    }
</script>
</html>
```

## Use `Window.location.href.indexOf()` with `RegExp Match()` to check if URL contains a specific word in JavaScript

`Window.location.href.indexOf()` could be used with JavaScript `String.prototype.match()` method. The `match()` method retrieves the result of matching a string.

The matching string is output with an `alert()` function when the returned value is above zero (0). A further discussion on the `match()` method is available via [this reference](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/match).

Below is an illustration:

``` html
<html>
<head>
<script type="text/javascript">

url = window.location.href;
if( url.match(/desktop/i) ) {
   alert("Alert: Desktop!");
}
</script>
</head>
<body>
    <h1>Check if url contains Desktop</h1>
</body>
</html>
```
