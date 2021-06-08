# [Headless CMS] Setting up a headless CMS

- **What is a headless CMS?** 
  - is a back-end-only **content management system** that acts primarily as a **content repository**.
  - headless means that there is no frontend
  - It makes content accessible via an **API** for display on any device, without a built-in front-end or presentation layer.
  - you can only update content types, fields, update data
  - Purpose:  storing and delivering structured content.



- **Headless CMS vs regular CMS**

![Regular and Monolithic CMS](https://img.storyblok.com/FYxbIsIqmOGJBSUUWnlHNkgPTUY=/840x0/filters:filters:fill(FFFFFF):filters:format(jpeg)/f/51376/4867x1562/fb7250cf1b/regular-and-monolithic-cms.jpg)

![Storyblok: Headless CMS](https://img.storyblok.com/s81JK_XdAyzWwyEC7bHNF3gDvEA=/840x0/filters:filters:fill(FFFFFF):filters:format(jpeg)/f/51376/4867x1562/8d59898080/headless-cms-explained-storyblok.jpg)



- **Sanity API and Sanity studio?** 
  - **Sanity API:** we interact with it.
  - **Sanity Studio:** it is the UI that we log into and where we can read/update/delete our data. 



- **Creating our own schema**:

- We can create our own schema under `schemas/` in which we export an object that has a bunch of data

```js
// An icon from material design
import { MdLocalPizza as icon } from 'react-icons/md';

export default {
  // Computer name
  name: 'pizza',
  // visible title
  title: 'Pizzas',
  type: 'document',
  icon,
  fields: [
    {
      name: 'name',
      title: 'Pizza Name',
      type: 'string',
      description: 'Name of the Pizza',
    },
  ],
};
```

We then import our schema in `schema.js` and pass the reference to our schema...

```js
import pizza from './pizza';

export default createSchema({
  // We name our schema
  name: 'default',
  // Then proceed to concatenate our document type
  // to the ones provided by any plugins that are installed
  types: schemaTypes.concat([pizza]),
});
```

When we save, it gives us

![image-20210512183445390](/Users/elenamartinezmarin/Library/Application Support/typora-user-images/image-20210512183445390.png)

it allow us to create a new pizza:

![image-20210512184030672](/Users/elenamartinezmarin/Library/Application Support/typora-user-images/image-20210512184030672.png)



- **Creating a slug for pizzas**

```js
import { MdLocalPizza as icon } from 'react-icons/md';

export default {
  // Computer name
  name: 'pizza',
  // visible title
  title: 'Pizzas',
  type: 'document',
  icon,
  fields: [
    {
      name: 'name',
      title: 'Pizza Name',
      type: 'string',
      description: 'Name of the Pizza',
    },
    {
      name: 'slug',
      title: 'Slug',
      type: 'slug',
      options: {
        // we specify that the source of the slug comes frmo the name
        source: 'name',
        maxLength: 100,
      },
    },
  ],
};
```

Now we can add a pizza and a slug

![image-20210512184218669](/Users/elenamartinezmarin/Library/Application Support/typora-user-images/image-20210512184218669.png)



- **[Concept] headless technology**
  - The term "headless" refers to removing the dependency of knowing where data will be displayed and instead just holding the data to be used wherever the developer chooses. This is often used to describe a CMS where content can be entered, held, then where and how that content is displayed is decided separately.



---

- **Examples of Headless CMS:** https://jamstack.org/headless-cms/