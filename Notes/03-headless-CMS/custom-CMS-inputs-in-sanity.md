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

the new component we create gets props from sanity

```jsx
export default function PriceInput({ type, value, onChange, inputComponent }) {
  return (
    <div>
      <h2>{type.title}</h2>
      <p>{type.description}</p>
    </div>
  );
}

```



createPatchFrom, set and unset

```jsx
import React from 'react';
import PatchEvent, { set, unset } from 'part:@sanity/form-builder/patch-event';

function createPatchFrom(value) {
  PatchEvent.from(value === '' ? unset() : set(Number(value)));
}

export default function PriceInput({ type, value, onChange, inputComponent }) {
  return (
    <div>
      <h4>{type.title}</h4>
      <p>{type.description}</p>
      <input
        type={type.name}
        value={value}
        onChange={(ev) => createPatchFrom(ev.target.value)}
        ref={inputComponent}
      />
    </div>
  );
}
```





---

`Intl.NumberFormat('en-CA', {`

`style: 'currency',`

`currency: 'USD',})` is built in to the browser and its a good way of formatting money

