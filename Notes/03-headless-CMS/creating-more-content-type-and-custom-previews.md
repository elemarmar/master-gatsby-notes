# [Headless CMS] Creating the Toppings Content Type and custom previews



- **How to control what shows up in Sanity Studio?** 
  - If you want to specify which fields should be used for what, you can control this by adding a `preview` key to the type defined in the schema. 🔗 [Ref](https://www.sanity.io/docs/previews-list-views)
  - the `prepare` function transforms the selection however you like:

```js
[...],  
  preview: {
    select: {
      name: 'name',
      vegetarian: 'vegetarian',
    },
    prepare: ({ name, vegetarian }) => ({
      title: `${name} ${vegetarian ? '🍃' : ''}`,
    }),
  },
```



---

Docummentation for types: https://www.sanity.io/docs/schema-types

