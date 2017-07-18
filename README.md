# Front-End-Developer-guidelines
Front End Developer's Basic Guidelines

## Table of Contents
  - [HTML](#html)
  - [CSS](#css)
  - [Javascript](#javascript)
  - [Cross Browser Compatible](#cross-browser-compatible)
  - [IE 8](#ie-8)
  
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
   
## Cross Browser Compatible
1) Prefix css3 styles
   ```
   -moz- /* Firefox and other browsers using Mozilla's browser engine */
   -webkit- /* Safari, Chrome and browsers using the Webkit engine */
   -o- /* Opera */
   -ms- /* Internet Explorer (but not always) */
   ```
2) Reset - use [normalize.css](http://necolas.github.io/normalize.css/) 

3）Box Model - avoid padding with widths
   ```
   * { -webkit-box-sizing: border-box; /* Safari/Chrome, other WebKit */
   -moz-box-sizing: border-box; /* Firefox, other Gecko */
   box-sizing: border-box; }
   ```
4) Clear floats
   ```
   .clearfix:after { 
      content: "."; 
      visibility: hidden; 
      display: block; 
      height: 0; 
      clear: both;
   }
   ```


 
## IE 8 
    
    a) HTML
       - Some of the new elements that HTML5 includes that IE8 doesn’t support
       ```
       section, article, nav, header, footer, aside, and canvas
       ```
       ```
       header, section, footer, aside, nav, main, article, figure {
          display: block; 
       }
       ```
       
    b) CSS
       - No media queries
       - No keyframes
       - Do not support transform or transition
       - No nth-of-type or nth-child selectors
       - Bootstrap do not support IE8
       
    c) Javascript
       - Angular, React – none of the most recent versions of any of these support IE8
 
