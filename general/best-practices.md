# Best practices

## Favor composition

* Any part of a layout is a composition of components,
* Any composition may be a composite for another composition,
* Nested composition makes complex layouts simple and beautiful.

## Responsive areas

You can render an area conditionally by defining it in the template string for the respective breakpoint.

```jsx
import { Composition } from 'atomic-layout'

const mobileTemplate = `
    'header'
    'content'
`

const desktopTemplate = `
    'header'
    'actions'
    'content'
`

<Composition
    template={mobileTemplate}
    templateLg={desktopTemplate} />
```

In the example above, `<Actions/>` area will be conditionally rendered only for the provided breakpoint \(`lg`\) **and up** \(see Breakpoints behavior\). We are using [`react-responsive`](https://github.com/contra/react-responsive) package to achieve conditional rendering.

## Custom breakpoints

[Set custom breakpoints](../api/layout/configure.md#breakpoints) to reflect the required screen sizes, orientation or resolution.

