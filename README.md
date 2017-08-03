# Front-End-Developer-guidelines
Front End Developer's Basic Guidelines

## Table of Contents
  - [HTML](#html)
  - [CSS](#css)
  - [Javascript](#javascript)
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
    - Heeader and Footer
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
   
 5）Favorite CSS3 Feature
    - Webfonts
    - Media Query
    - Multile Backgrounds
    - Box Shadows
   
## Javascript
1) Scope: Local and Global
2) Asynchronous JavaScript And XML (AJAX): is a way to communicate to the server without reloading the page. It uses ```XMLHttpRequest``` to communicate to a server-side script to retrieve data formatted in JSON, XML, HTML, or plain text. 
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

4) Traverse DOM
   
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


