

```css
  li {
    --rotate: -2deg;
    transform: rotate(var(--rotate));
    order: 1;
  }
  li:nth-child(1) {
    --rotate: 1deg;
  }
```

instead of creating again the css rule we can simply update the variable value. 

clamp

  font-size: clamp(1px, 0.65vw, 8px);



----

tools:

Gatsby-cli

sanity-cli

sudo npm install Gatsby-cli @sanity/cli -g





investigar qué es gatsby y por qué es tan guay



pages in gatsby

Gatsby automatically converts react components in `src/pages` into pages.

- `src/pages/about.js` would be accessed `/about`

  public: directory as gatsby is building itself and eventually when we deploy and run build on gatsby

  src: most of the gatsby will live. The only folder that is gatsby specific is the `pages` folder. (Other folders made up)

  ![image-20210505231550930](file:///Users/elenamartinezmarin/Library/Application%20Support/typora-user-images/image-20210505231550930.png?lastModify=1620427678)

  - pages can be dynamically gnerated 
  - they can be done based on file system routing: 

  static: where you put files that you simply want to be served (favicon). Almost always you don't want to put a file in static even if it's a pic, css, etc.  -- "everything must go through gatsby" (must be importer through gatsby) (css, images, js) because then gatsby knows about your assets and can do cool things with them. (performance, speed):

  

  `.gitkeep` exists so that git doesn't delete the empty directory.

  

  templates: similar to pages but are reusable 

  

  hot reloading

  

  