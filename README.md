# Front-End-Developer-guidelines
Front End Developer's Basic Guidelines

## Table of Contents
  - [HTML](#html)
  - [CSS](#css)
  - [Javascript](#javascript)
  - [Cross Browser Compatible](#cross-browser-compatible)
  
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
 
 1) IE 8 
    
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
 
