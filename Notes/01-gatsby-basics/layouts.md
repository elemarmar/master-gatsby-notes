# [Gatsby Basics] Creating Layouts in Gatsby

- **Example of a gatsby project structure**

  ```
  |-- /.cache
  |-- /plugins
  |-- /public
  |-- /src
      |-- /pages
      |-- /templates
      |-- html.js
  |-- /static
  |-- gatsby-config.js
  |-- gatsby-node.js
  |-- gatsby-ssr.js
  |-- gatsby-browser.js
  ```

  

  - `gatsby-config.js` 
    - — configure options for a Gatsby site, with metadata for project title, description, plugins, etc.

  

  - `gatsby-node.js` 
    - — implement Gatsby’s Node.js APIs to customize and extend default settings affecting the build process

  

  - `gatsby-browser.js`
    -  — customize and extend default settings affecting the browser, using Gatsby’s browser APIs

  

  - `gatsby-ssr.js`
    -  — use Gatsby’s server-side rendering APIs to customize default settings affecting server-side rendering



- **What's a layout?** 
  - something that is either in all pages or in most of them. 
  - It’s common to wrap pages with a React layout component, which makes it  possible to share markup, styles, and functionality across multiple  pages.



- **Is there any special thing for layouts in Gatsby?**
  - Gatsby does not, by default, automatically apply layouts to pages.  Instead, Gatsby follows React’s compositional model of importing and using components.



- **If we want to wrap all of our pages in a layout component, what is best practice in Gatsby? **

  - Instead of wrapping every single page in Layout component, we use gatsby custom files (`gatsby-browser` and `gatsby-ssr`) that will automatically wrap them.

    1. we go to our gatsby main folder (not inside of `src`) but the root folder and we create the file `gatsby-browser.js`
    2. we use the `wrapPageElement` function to set the wrapper component around the page elements that won't get unmounted on page changes. 

    ```jsx
    // gatsby-browser.js
    import React from 'react';
    import Layout from './src/components/Layout';
    
    export function wrapPageElement({ element, props }) {
      return <Layout {...props}>{element}</Layout>;
    }
    ```

    >  ⚠️ you have to quit the build and restart it to see changes. 

    3. we also need to create a file root `gatsby-ssr.js` with same content




- **What is `gatsby-browser.js`?**
  - It is a file that lets you (1) respond to Gatsby-specific events within the browser, and (2) wrap your page components in additional global components. 
  - It allows you to use Browser APIs: export each API you want to use from `gatsby-browser.js`



- **Where to use the API wrapPageElement?**  `gatsby-browser.js` vs  `gatsby-ssr.js`

  - You generally should implement the same components in both `gatsby-ssr.js` and `gatsby-browser.js` so that pages generated through SSR are the same after being [hydrated](https://www.gatsbyjs.com/docs/glossary#hydration) in the browser.

  

- **Difference between gatsby-browser and gatsby SSR**
  - `gatsby-browser` runs once the page has been loaded (hydration)
  - `gatsby-ssr` generates everything on the server (fast). It lets you alter the content of static HTML files as they are being Server-Side Rendered by Gatsby and Node.js.



- [Concept] **What is Hydration?**
  - Once a site has been [built](https://www.gatsbyjs.com/docs/glossary#build) by Gatsby and loaded in a web browser, [client-side](https://www.gatsbyjs.com/docs/glossary#client-side) JavaScript assets will download and turn the site into a full React application that can manipulate the [DOM](https://www.gatsbyjs.com/docs/glossary#dom). This process is often called re-hydration as it runs some of the same  JavaScript code used to generate Gatsby pages, but this time with  browser DOM APIs like `window` available.



- [Concept] **JAMStack**
  - JAMStack refers to a modern web architecture using [JavaScript](https://www.gatsbyjs.com/docs/glossary#javascript), [APIs](https://www.gatsbyjs.com/docs/glossary#api), and ([HTML](https://www.gatsbyjs.com/docs/glossary#html)) markup. From [JAMStack.org](https://jamstack.org): “It’s a new way of building websites and apps that delivers better  performance, higher security, lower cost of scaling, and a better  developer experience.”s