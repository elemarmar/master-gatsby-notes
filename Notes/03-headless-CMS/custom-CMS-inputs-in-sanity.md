Custom input components in gatsby



we create a folder called `components` where we will create all our custom input components.



- import the component in the schema we want
- use it in the config 

```js
    {
      name: 'price',
      title: 'Price',
      type: 'number',
      description: 'Price of the pizza in cents',
      validation: (Rule) => Rule.min(1000).max(500000),
      inputComponent: PriceInput, // 👈🏻
    },
```

