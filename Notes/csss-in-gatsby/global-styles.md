# [CSS in Gatsby] Global Styles

- Gatsby needs to know aout everything in your project (imgs, pages, links, data, css) - all css will be dumpued before any of the content. gatsby figures out what css is necessary (critical css) in order for the page to render.



- Ways to add css

  - Create css inside of styles folder
  - 1. import it in browser-gatsby.js

  ```js
  import './src/styles/red.css';
  ```

  2. CSS modules
  3. Styled components: scoped css in react applications



- why importing images in js to use them in styles and not reference them with a path? because then they would have to go into the static folder and gatsby wouldn't kno wabout them. 



- how to select gatsby images before they are fully rendered?

  - (review)

  ```js
  .gatsby-image-wrapper img[src*=base64\\,] {
    // Styles here
  }
  ```

- - gatsby takes the svg, puts it through its compressor,e tc and puts a unique identifier on it. 

----

1. Setting global styles: colors, fonts, buttons, scrollbars, etc. 
2. Reset css with normalize.css



- what gatsby does with images