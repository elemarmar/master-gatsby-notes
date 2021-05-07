# [Gatsby Basics] Creating Layouts in Gatsby

- Layout something that is either in all pages or in most of them. 
- There is no special thing for layouts in Gatsby. 



- ==Explain a bit more a simple layout==



- **If we want to wrap all of our pages in a layout component, what is best practice in Gatsby? **

  - instead of wrapping in every single page. USe gatsby custm files that will automatically wrap them around us -- they are the "Gatsby browser" and the Gatsby SSR files.

  - 1. we go to our gatsby main folder (not inside of src) but root. create file gatsby-browser.js

    2. we use the wrap page element hook and gatsby will automatically do that for us so that we don't have to manually wrap our pages in a layout 

    3. we create a function wrapPageElement -- create our own little plugin that anytime gatsby renders out a page, it will wrap that in sth.

       ```js
       import React from 'react';
       
       export function wrapPageElement({ element, props }) {
         return <div>😀</div>;
       }
       ```

       - ⚠️ you have to quit the build and restart it to see changes. 

    4. we also need to create a file root gatsby-ssr.js copy same there 



- **What is gatsby-browser.js?**
  - It is a specific Gatsby file that allows us to hook into different Gatsby APIs.



- **Difference between gatsby-browser and gatsby SSR**
  - Gatsby browser runs once the page has been loaded
  - gatsby also generates everything on the server (fast)



---

check

https://www.gatsbyjs.com/docs/reference/config-files/gatsby-browser/

https://www.gatsbyjs.com/docs/reference/config-files/gatsby-ssr/

https://www.gatsbyjs.com/docs/how-to/routing/layout-components/

https://www.gatsbyjs.com/docs/recipes/pages-layouts/