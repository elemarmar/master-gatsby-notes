# [Gatsby Basics] Creating Layouts in Gatsby

### Gatsby project structure

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

> This is an example.

<details>
  <summary><b>What is <code>gatsby-config.js</code>?</b></summary>
  It's a file that handles the configure options for a Gatsby site, with metadata for project title, description, plugins, etc.
</details>

<details>
  <summary><b>What is <code>gatsby-node.js</code>?</b></summary>
  It is a file that implements Gatby's <b>Node.js API</b> to customize and extend default settings affecting the <b>build process</b>.
</details>

<details>
  <summary><b>What is <code>gatsby-browser.js</code>?</b></summary>
  It's a file that implements Gatsby's <b>browser API</b> to customize and extend default settings affecting the <b>browsers</b>.
</details>

<details>
  <summary><b>What is <code>gatsby-ssr.js</code>?</b></summary>
  It's afile that implements Gatsby's server-side rendering APIs to customize default settings affecting <b>server-side rendering</b>.
</details>

<details><summary><b>Difference between gatsby-browser and gatsby ssr</b></summary>
  <li><code>gatsby-browser</code> runs once the page has been loaded (hydration)</li>
  <li>
    <code>gatsby-ssr</code> generates everything on the server (fast). Itl ets you alter the content of static HTML files as they are being Server-Side Rendered by Gatsby and Node.js.
  </li>
</details>

---

### Layouts

<details>
  <summary><b>What's a layout?</b></summary>
  <ul>
    <li>It's a structure that is either in all pages or in most of them.</li>
    <li>It's common to wrap pages with a React layout component, which makes it possible to share markup, styles, and functionality across multiple pages.</li>
  </ul>
</details>

<details>
  <summary><b>Is there any special thing for layouts in Gatsby?</b></summary>
  Gatsby does not, by default, automatically apply layouts to pages. Instead, Gatsby follows React's compositional model of importing and using components.
</details>

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

<details>
  <summary><b>Where to use <code>wrapPageElement</code> function?</b></summary>
  In <code>gatsby-browser.js</code> and <code>gatsby-ssr.js</code>. You generally should implement the same components in both files so that pages generated through SSR are the same after being <b><i>hydrated</i></b> in the browser.
</details>

---

### Concepts

<details>
  <summary><b>What is Hydration?</b></summary>
  Once a site has been built by Gatsby and loaded in a web browser, client-side JavaScript assets will download and turn the site into a full React application that can manipulate the DOM. This process is often called re-hydration as it runs some of the same  JavaScript code used to generate Gatsby pages, but this time with  browser DOM APIs like <code>window</code> available.
</details>

<details>
  <summary><b>What is JAMStack?</b></summary>
  JAMStack refers to a modern web architecture using JavaScrip, APIs, and HTML markup. From JAMStack.org: “It’s a new way of building websites and apps that delivers better  performance, higher security, lower cost of scaling, and a better  developer experience.”s
</details>