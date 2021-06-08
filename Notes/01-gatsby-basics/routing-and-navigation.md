# [Gatsby Basics] Routing and navigation in Gatsby

- **Why are components different from pages?**
  - **components** are reusable pieces of code that can be used within a **page**.



- **What do we use for internal navigation in Gatsby?**

  - Instead of using **regular anchor links** inside of gatsby we use (1) the **Link** component for creating links between internal pages and (2) `navigate` function for programmatic navigation.

  - ==A bit more information on difference between anchor link and Link component.== . because the link tag doesn't reload the page, it only "swaps" the content to display. 👉🏻 It does "<u>HTML5 push state</u>".

  - 🔗 [Gatsby](https://www.gatsbyjs.com/docs/reference/built-in-components/gatsby-link/)


  

- **What is the Link component in Gatsby?**

  - It is a wrapper around the Reach Router Link that adds enhancements specific to Gatsby. 
  - ℹ️ Reach Router is a simple router for React that borrows from React Router, among others. 

  

- **What is HTML5 pusState?**
  - The `history.pushState()` method adds an entry to the browser's session history stack. HTML five push state: changes the URL bar + gives back history in the browser.
  - 🔗 [MDN](https://developer.mozilla.org/en-US/docs/Web/API/History/pushState) [CSS Tricks](https://css-tricks.com/using-the-html5-history-api/)



- **What's the HTML5 History AIP?**

  - It's an API that allows us to modify a website's URL without a full page refresh.
  - It is useful for loading portions of a page with JS.
  - 🔗 [MDN](https://developer.mozilla.org/en-US/docs/Web/API/History_API) [CSS Tricks](https://css-tricks.com/using-the-html5-history-api/)

  

- **What is the Link tag in Gatsby?**
  - The link tag will render an anchor link but it is "supercharged" (loaded w/ js needed to swap the content without having to reload page. It also does <u>HTML5 push state.</u>)



- **Difference between declarative and imperative in react.**
  - **declarative:** we declare how it works
  - **imperative**: we don't declare how it works you write the code as to what happens as a result of sth else (e.g. what happens after a form is submitted)



- **How to programatically navigate to a page in Gatsby?** with 

  - With `navigate`. 

  ```js
  import { navigate } from 'gatsby'; 
  
  const goToHeaven = () {
    setTimeout(() => {
      navigate('/heaven');
    }, 2000);
  }
  ```

  

- **How to add browser history when using navigate?** 

  ```js
  navigate('/languages', { replace: true });
  ```

  **hello** <strong>hello</strong> 
  
  > Hellos this is **hello there **

---

Articles to review;

- On History API: https://css-tricks.com/using-the-html5-history-api/ + https://developer.mozilla.org/en-US/docs/Web/API/History_API
- Gatsby Link API: https://www.gatsbyjs.com/docs/reference/built-in-components/gatsby-link/

https://stackoverflow.com/questions/33655534/difference-between-declarative-and-imperative-in-react-js