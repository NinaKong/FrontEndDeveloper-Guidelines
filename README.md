# Front-End-Developer-guidelines
Front End Developer's Basic Guidelines

## Table of Contents
  - [HTML](#html)
  - [CSS](#css)
  - [Javascript](#javascript)
  - [DOM](#dom)
  - [Cross Browser Compatible](#cross-browser-compatible)
  - [IE 8](#ie-8)
  - [Code Standards](#code-standards)
  - [Network](#network)

## HTML
1) Doctype
   ```
   <!DOCTYPE html>
   ```
   The  ```<!DOCTYPE> ``` is not an HTML tag, it lets the web browser know the HTML version in the web page. It is the first thing in the HTML file.

2）Favorite HTML5 Feature

  - Audio and Video

  - Section

  - Header and Footer

  - Nav



## CSS
1) Specificity  
   Style attribute from most to least：
   ```
   specific (inline style) > ID > Class [pseudo-class, attribute] > Elements
   ```
   pseudo-class:
   ```  
   a:link, a:visited
   ```
   pseudo-element selector: 
   ```
   div:first-letter, div:before
   ```
  
2) Cascade
   
   - Importance
   ```
   <div class="movie" id="starwars">Star Wars</div>
   ```
   ```
   #starwars {
     border: 1px solid #000000;
   }
   .movie {
     border: none !important;
   }
   ```
   Note: Do not recommend
   - Specificity
   
   - Source order
   ```
   p {
      color: #000000;
   }
   p {
      color: #cccccc;
   }
   ```
3) Box Model: content, padding, border, and margin
   - Content: The text or image content of the box
   - Padding: an area around the content
   - Border: A border that goes around the padding and content
   - Margin: an area outside the border
   
   Note: The padding and margin are transparent
   
4) Display
   ```
   display: inline;
   ```
   The elements like ```<span>```, ```<em>```, or ```<b>```. 
   margin-top, margin-bottom, padding-top, padding-bottom, width, and heigh will not work.
   ```
   display: inline-block;
   ```
   margin-top, margin-bottom, padding-top, padding-bottom, width, and heigh will be respected.
   
5) Favorite CSS3 Feature

    - Webfonts
    - Media Query
    - Multile Backgrounds
    - Box Shadows


6) [Clear Float](https://css-tricks.com/all-about-floats/)
  
   - Collapse
     ```
     overflow: hidden;
     ```
     If parent element only contained floated elements, the height would be collapsed. If there is no background color, it will not be obvious.
   
   - Clearfix
     ```
     .clearfix:after {
        content: ".";
        visibility: hidden;
        display: block;
        height: 0;
        clear: both;
     }
     ```
     
7) CSS preprocessor
    - Nesting
    - Variables
    - Math Function
      ```
         .medium {
             padding: @base-padding * 1.5;
         }
      ```
    - Operational Functions
      ```
          p{
              color: darken(@primary-color);
          }
      ```
    
    - Mixins: reusable
    
    - Separate your code to different files
      ```
          @import “variables.less”;
          @import “mixins.less”;
          @import “buttons.less”;
          @import “site.less”;
      ```

8) Hide Content

      | Hide Elements | Opacity | Visibility | Display |
      | ------------- | ------------- | ------------- | ------------- | 
      | CSS  |  ```opacity: 0;```  |  ```visibility: hidden;``` | ```display: none;``` |
      | Screen Reader  |  Show  |  Hide | Hide |
      | Original Space | Hide  | Show  | Show |
      | Descendants | Show  | Show  | Hide |

9) [Block Formatting Context](https://www.sitepoint.com/understanding-block-formatting-contexts-in-css/)

   - float is not none
   - position is neither static nor relative
   - display is table-cell, table-caption, inline-block, flex, or inline-flex
   - overflow is not visible

10) [Box-sizing](https://css-tricks.com/box-sizing/)
    ```
    html {
      -webkit-box-sizing: border-box;
      -moz-box-sizing: border-box;
      box-sizing: border-box;
    }
    *, *:before, *:after {
      -webkit-box-sizing: inherit;
      -moz-box-sizing: inherit;
      box-sizing: inherit;
    }
    ```
    
    - The padding and border of that element no longer increase its width
    - Very convenient for column layouts
    - Mix percentage and pixel values


## Javascript
1) Scope: Local and Global
2) [Asynchronous JavaScript And XML (AJAX)](https://www.w3schools.com/xml/ajax_intro.asp): is a way to communicate to the server without reloading the page. It uses         
   - Steps
      - 1. An event occurs in a web page (the page is loaded, a button is clicked)
      - 2. An XMLHttpRequest object is created by JavaScript
      - 3. The XMLHttpRequest object sends a request to a web server
      - 4. The server processes the request
      - 5. The server sends a response back to the web page
      - 6. The response is read by JavaScript
      - 7. Proper action (like page update) is performed by JavaScript
      
      ```XMLHttpRequest``` to communicate to a server-side script to retrieve data formatted in JSON, XML, HTML, or plain text. 
   
   - Advantages
     
     a) Reduce the traffic travels between the client and the server
     
     b) Increases performance and speed with faster response time
     
   - Disadvantages
     
     a) Increase design and development time
     
3) Basic Knowlege: use for widgets
   - Dropdown
     ```
     function myFunction() {
         document.getElementById("myDropdown").classList.toggle("show");
     }
     ```
     ```classList```: returns the class name(s) of an element, it is useful to add, remove and toggle CSS classes on an element.

     ```toggle```: between hiding and showing an element.

   - Tab
     ```
     event.currentTarget.className += " active";
     ```   
     ```   
     <body onclick="targetFunction(event)">

        <p>current target</p>

        <p><strong>Note:</strong> only target</p>
     </body>
     ```   
     ```currentTarget```: returns the element whose event listeners triggered the event, even though it is useful during capturing and bubbling. In the example above, it will only return body, even though you click ``` <p>``` or ```<strong>```  tag.

     ```target```: returns the element that triggered the event. In the example above, it will return the event you triggered.
   - Accordions  
   ```nextElementSibling```: returns the element immediately following the specified element

4) Asynchronous JavaScript And XML(AJAX)
   - Combination of: A browser built-in XMLHttpRequest object (to request data from a web server)
JavaScript and HTML DOM (to display or use the data)
   - Update a web page without reloading the page
   - Request data from a server - after the page has loaded
   - Receive data from a server - after the page has loaded
   - Send data to a server - in the background
     ```
        var data = new XMLHttpRequest();
        data.open("GET", "http://api.wunderground.com/api/0def10027afaebb7/conditions/q/FL/Boca_Raton.json", true);
        //http://stackoverflow.com/questions/16592709/using-javascript-to-add-custom-http-header-and-trigger-file-download
        data.setRequestHeader('Authorization', 'token');
        data.setRequestHeader('Content-Type', 'application/json');
        data.setRequestHeader('Accept-Encoding', 'application/json');
        //The onload event occurs when an object has been loaded.
        data.onload = function() {
            if (data.status === 200) {
                alert('Request success');
            }
            else {
                alert('Request failed.  Returned status of ' + data.status);
            }
        };
        data.send();
        var results = JSON.parse(data.response);
        var weather = "Location:" + results.current_observation.display_location.full;
        var temp = "Temperature:" + results.current_observation.temperature_string;
        var state = "State:" + results.current_observation.icon;
        getWeather("weather", weather);
        getWeather("temp", temp);
        getWeather("state", state);
        function getWeather(arg1, arg2) {
            document.getElementById(arg1).innerHTML = arg2;
        }
     ```
   
5) Loop 
   - ```for```: loops through a block of code a number of times
     ```
       for (i = 0; i < cars.length; i++) { 
          //
       }
     ```
   
   - ```.map()```: creates a new array with the results of calling a function for every array element.
     ```
        var arr = [25, 64, 81, 100];
        function myFunction() {
          document.getElementById("example").innerHTML = arr.map(Math.sqrt);
        }
     ```
   
   - ```.filter()```: creates an array filled with all array elements that pass a test (provided as a function).
     ```
        var scores = [32, 63, 76, 90];

        function checkScores(score) {
            return score >= 60;
        }

        function myFunction() {
            document.getElementById("example").innerHTML = scores.filter(checkScores);
        }
     ```
   
6) [Hoisting](http://adripofjavascript.com/blog/drips/variable-and-function-hoisting)
   
   - Variables
     ```
        // Outputs: undefined
        console.log(declaredLater);

        var declaredLater = "Now it's defined!";

        // Outputs: "Now it's defined!"
        console.log(declaredLater);
     ```
   
   is equal to:
   
     ```
        var declaredLater;

        // Outputs: undefined
        console.log(declaredLater);

        declaredLater = "Now it's defined!";

        // Outputs: "Now it's defined!"
        console.log(declaredLater);
     ```
   
   - Functions
     ```
        // Outputs: "Yes!"
        isItHoisted();

        function isItHoisted() {
          console.log("Yes!");
        }
     ```
     is equal to:
   
     ```
        function isItHoisted() {
          console.log("Yes!");
        }
        // Outputs: "Yes!"
        isItHoisted();
     ```
   
   
   Note: function definition hoisting only occurs for function declarations, not function expressions. 
     ```    
        // Outputs: "Definition hoisted!"
        definitionHoisted();

        // TypeError: undefined is not a function
        definitionNotHoisted();

        function definitionHoisted() {
          console.log("Definition hoisted!");
        }

        var definitionNotHoisted = function () {
          console.log("Definition not hoisted!");
        };
      ```
    
7) Function Declarations and Function Expressions

   - Function Declarations: named function variable without requiring variable assignment
   
     ```
        function bar() {
          return 5;
        }
     ```
   
   - Function Expressions: a function as a part of an variable assignment
   
     ```
        //anonymous function expression
        var a = function () {
          return 5;
        }
        //named function expression
        var a = function bar() {
          return 5;
        }
        //self invoking function expression
        (function sayHelloWorld() {
            alert("hello world!");
        })();
     ```

8) [Closure](https://www.w3schools.com/js/js_function_closures.asp): an inner function that has access to the outer (enclosing) function’s variables—scope chain
   
   - access to its own scope
   
   - access to the outer function’s variables
   
   - access to the global variables
   
     ```
        function animal(petname) {
            return function() {
                return petname;
            }
        }
     ```
9) [Promise](https://davidwalsh.name/promises) and (https://scotch.io/tutorials/javascript-promises-for-dummies)

   - States
   
     a) Pending: it can transition to the fulfilled or rejected state
     
     b) Fulfilled (resolve() was called)
     
     c) Rejected (rejected() was called)
     
 
   - Usage:
   
     a) setTimeout
     
     b) XMLHttpRequest
     
     c) provide resolve and reject
     
        ``` 
            var p = new Promise(function(resolve, reject) {

                // Do an async task async task and then...

                if(/* good condition */) {
                          resolve('Success!');
            }
            else {
                          reject('Failure!');
            }
            });

            p.then(function() {
                /* do something with the result */
            }).catch(function() {
                /* error :( */
            })
        ``` 
      
   - then: The then callback is triggered when the promise is resolved. 
        ```  
          new Promise(function(resolve, reject) {
              // A mock async action using setTimeout
              setTimeout(function() { resolve(10); }, 3000);
          })
          .then(function(result) {
              console.log(result);
          });

          // From the console:
          // 10
        ```

10) [HTTP Request](https://www.w3schools.com/jquery/jquery_ajax_get_post.asp): two commonly used methods for a request-response between a client and server
    - Example: A client (browser) submits an HTTP request to the server; then the server returns a response to the client. The response contains status information about the request and may also contain the requested content.
    - GET: requests data from a specified resource
    - POST: submits data to be processed to a specified resource
    
11) [Event Caputring and Event Bubbling](https://stackoverflow.com/questions/4616694/what-is-event-bubbling-and-capturing)

    - Example
      ```
        <div>
            <ul>
                <li></li>
            </ul>
        </div>
      ```
      
      Caputring - div -> ul -> li
      
      Bubbling - li -> ul -> div
    
    - event target
      ```
        <div  onclick="">
            <ul>
                <li></li>
            </ul>
        </div>
      ```

      event.currentTarget - div, it is the hander runs on
      
      event.target - is the inside element that was clicked actually
    
    - use addEventListener: attaches an event handler to the document.
      ```
      document.addEventListener("click", function(){
          document.getElementById("example").innerHTML = "Hello World";
      });
      ```
       - true - The event handler is executed in the capturing phase
       
       - false- Default. The event handler is executed in the bubbling phase
       
    
    - Stop Bubbling - event.stopPropagation()
      ```
        <div onclick="">
          <button onclick="event.stopPropagation()">Submit</button>
        </div> 
      ```
      
   

12) Performance: touching the DOM can be expensive when you have many nodes, use document fragments

    - createDocumentFragment: creates a imaginary Node object, with all the properties and methods of the Node object.
    
    - createElement: creates an Element Node with the specified name.
    
    - appends a node as the last child of a node.

      ```
        <div id="container"></div>
      ```
      ```
        var target = document.getElementById("container"); 
        //avoid to add text in a loop structure in html
        //should add these to a document fragment, and append that fragment once finished
        //This approach mutates the DOM only once
        function createDiv (array) { 
          var fragment = 		document.createDocumentFragment(); 
          for (var i = 0; i < array.length; i++) { 
            var div = document.createElement("div"); 
            div.innerHTML = array[i]; 
            fragment.appendChild(div); 
        } 
          target.appendChild(fragment); 
        }
        var example = ["Nina", "Meow", "Yehua"];
        createDiv(example);
      ```
      
13) this
    - call: calls a function with a given this value and arguments provided individually.
    - apply: calls a function with a given this value, and arguments provided as an array (or an array-like object).
    - bind: creates a new function that, when called, has its this keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.
    
    Note: if know how many arguments should use ```.call```, if do not know or araguments are an array, should use ```.apply```
    
14) [null, undefined, and undeclared](http://lucybain.com/blog/2014/null-undefined-undeclared/)
    - ```undeclared``` variables don’t even exist
    - ```undefined``` variables exist, but don’t have anything assigned to them
    - ```null``` variables exist and have null assigned to them

15) == vs ===: if using the triple equals, the values must be equal in type as well
    
## DOM
1) Traverse DOM
   
   - Select and find nodes
     
     
     ```querySelector```: returns the first element that matches a specified CSS selector(s) in the document
     
     ```document.querySelector(".example");```
     
     
     
     
     ```querySelectorAll```: returns all elements in the document that matches a specified CSS selector(s), as a static NodeList object.
     
     ```document.querySelectorAll(".example");```
     
     
     
     ```getElementsByClassName```: returns a collection of all elements in the document with the specified class name, as a NodeList object.
     ```document.getElementsByClassName("example");```
     
     
   - Traverse up and down
   
     
     ```parentNode```: returns the parent node of the specified node, as a Node object.
     
     ```document.getElementById("example").parentNode.nodeName;```
     
     
     
     ```childNodes[nodenumber]```:returns a collection of a node's child nodes, as a NodeList object.
     ```document.getElementById("example").childNodes[2].text;```
     
     
     ```firstChild```: returns the first child node of the specified node, as a Node object.

     ```document.getElementById("example").firstChild.innerHTML;```
     
     
     
     ```lastChild```:returns the last child node of the specified node, as a Node object.
     ```document.getElementById("example").lastChild.innerHTML;```
     
     
   - Traverse left and right
         
     ```nextSibling```: returns the node immediately following the specified node, in the same tree level.
     ```document.getElementById("example").nextSibling.innerHTML;```
      
      
     ```previousSibling```: returns the previous node of the specified node, in the same tree level.
     ```document.getElementById("example").previousSibling.innerHTML;```
   
   
## Cross Browser Compatible
1) Prefix CSS styles
   ```
   -moz- /* Firefox and other browsers using Mozilla's browser engine */
   -webkit- /* Safari, Chrome and browsers using the Webkit engine */
   -o- /* Opera */
   -ms- /* Internet Explorer (but not always) */
   ```

2) Reset - use [normalize.css](http://necolas.github.io/normalize.css/) 
 
3) Clear floats
   ```
   .clearfix:after { 
      content: "."; 
      visibility: hidden; 
      display: block; 
      height: 0; 
      clear: both;
   }
   ```
   
4) Box Model - avoid padding with widths
   ```
   * { 
      -webkit-box-sizing: border-box; /* Safari/Chrome, other WebKit */
      -moz-box-sizing: border-box; /* Firefox, other Gecko */
      box-sizing: border-box; 
   }
   ```
 
5) Graceful degradation and progressive enhancement
 
## IE 8 
    
1) HTML
   - Some of the new elements that HTML5 includes that IE8 doesn’t support
   ```
   section, article, nav, header, footer, aside, and canvas
   ```
   ```
      header, section, footer, aside, nav, main, article, figure {
      display: block; 
   }
   ```
       
2) CSS
   - No media queries
   - No keyframes
   - Do not support transform or transition
   - No nth-of-type or nth-child selectors
   - Bootstrap do not support IE8
       
3) Javascript
   - Angular, React – none of the most recent versions of any of these support IE8
 
## Code Standards
1) Progressive Enhancement
2) Team members keep consistency and conventions
3) Solutions should be as simple and clear as possible
4) Readable code is critical
5) Avoid in-line styles and in-line JavaScript whenever possible

## Network
1) [Type a URL in browser](http://edusagar.com/articles/view/70/What-happens-when-you-type-a-URL-in-browser)

   - Step 1. Type URL in the browser
   - Step 2. If requested object is in browser cache and is fresh, move on to Step  8.
   - Step 3. Domain Name System (DNS) lookup to find the ip address of the server
   - Step 4. Browser initiates a Transmission Control Protocol (TCP) connection with the server.
   - Step 5. Browser sends a HTTP request to the server.
   - Step 6. Server handles the incoming request
   - Step 7. Browser receives the HTTP response
   - Step 8. Browsers displays the html content
   - Step 9. Client interaction with server

2) [eTag](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/ETag)
   - The ETag HTTP response header is an identifier for a specific version of a resource.
   - If the content has changed, etags are useful to help prevent simultaneous updates of a resource from overwriting each other.
   - If the resource at a given URL changes, a new Etag value must be generated. Etags are therefore similar to fingerprints and might also be used for tracking purposes by some servers.
   
3) [Same-origin Policy](http://lucybain.com/blog/2014/same-origin-policy/)
   - the protocol (http vs. https)
   - the domain (subdomain.yoursite.com vs. yoursite.com vs. google.com)
   - the port (:80 vs. :4567)
