### [HTML DOM](https://www.w3schools.com/js/js_htmldom.asp)

The HTML DOM model is constructed as a tree of Objects:

![HTMLDOM](../assests/htmltree.gif)

The HTML DOM is a standard for how to get, change, add, or delete HTML elements.

The HTML DOM Document Object

The document object represents your web page.

### [Web Worker](https://www.w3schools.com/js/js_api_web_workers.asp)

A web worker is a JavaScript running in the background, without affecting the performance of the page.

```html
<!DOCTYPE html>
<html>
  <body>
    <p>Count numbers: <output id="result"></output></p>
    <button onclick="startWorker()">Start Worker</button>
    <button onclick="stopWorker()">Stop Worker</button>

    <script>
      let w;

      function startWorker() {
        if (typeof w == "undefined") {
          w = new Worker("demo_workers.js");
        }
        w.onmessage = function (event) {
          document.getElementById("result").innerHTML = event.data;
        };
      }

      function stopWorker() {
        w.terminate();
        w = undefined;
      }
    </script>
  </body>
</html>
```

#### Web Workers and the DOM

Since web workers are in external files, they do not have access to the following JavaScript objects:

- The window object
- The document object
- The parent object
