# Responsive layout

## Introduction

There are two main keys when creating a responsive layout:

1. Rendering layout areas conditionally,
2. Applying props \(`gutter`, `margin`, etc.\) conditionally on certain breakpoints.

## Responsive areas

### Declaration

Any grid area that is not present on all template declarations becomes responsive.

```jsx
const templateMobile = `
    'thumbnail'
    'heading'
    'subheading'
`

const templateDesktop = `
    'thumbnail heading'
    'thumbnail subheading'
    'thumbnail meta'
`
```

We have two template declarations above—one for mobile and one for desktop screens. Areas `thumbnail`, `heading` and `subheading` are present in both template declarations. However, the `meta` grid area is declared in `templateDesktop` only. This makes `meta` a responsive area.

### Breakpoints

Having different areas in different template declarations only signifies conditional areas. In order to control the breakpoints where those areas must be rendered, we need to pass templates declarations to the `template` props of the `Composition` component:

```jsx
import React from 'react'
import { Composition } from 'atomic-layout'

const templateMobile = `
    'thumbnail'
    'heading'
    'subheading'
`

const templateDesktop = `
    'thumbnail heading'
    'thumbnail subheading'
    'thumbnail meta'
`

const Card = () => (
    <Composition
        template={templateMobile}
        templateLg={templateDesktop}
        {({ Thumbnail, Heading, Subheading, Meta }) => (
            <React.Fragment>
                <Thumbnail>I am rendered always</Thumbnail>
                <Heading>I am rendered always</Heading>
                <Subheading>I am rendered always</Subheading>
                <Meta>I am rendered on "lg" breakpoint and up!</Meta>
            </React.Fragment>
        )}
    </Composition>
)

export default Card
```

The composition above will wrap `Meta` grid area in a `<MediaQuery/>` component from [react-responsive](https://github.com/contra/react-responsive), ensuring that it is rendered on `lg` breakpoint and up \(default breakpoint behavior\).

## Responsive props

Any prop name suffixed with a breakpoint name is a responsive prop. It implies that the prop's value will be applied on the given breakpoint.

We have already used a responsive prop in the example above. By suffixing `template` with the `lg`, we stated that the given value must be applied on the `lg` breakpoint and up. Following this example, let's create a different gutter between the grid areas on different breakpoints:

```jsx
<Composition
    template={templateMobile}
    templateLg={templateDesktop}
    gutter={10}
    gutterLg={20}
    {({ Thumbnail, Heading, Subheading, Meta }) => (
        <React.Fragment>
            <Thumbnail>I am rendered always</Thumbnail>
            <Heading>I am rendered always</Heading>
            <Subheading>I am rendered always</Subheading>
            <Meta>I am rendered on "lg" breakpoint and up!</Meta>
        </React.Fragment>
    )}
</Composition>
```

There are two props we have added: `gutter` and `gutterLg`.

* `gutter` adds a `grid-gap` of `10px` on mobile screens, since `xs` is the default breakpoint,
* `gutterLg` adds a `grid-gap` of `20px` on large screens and up, since `up` is the default behavior.

{% hint style="info" %}
You can configure [custom breakpoints](../../fundamentals/breakpoints.md#custom-breakpoints), default breakpoint and default behavior. Responsive props will abide by your settings.
{% endhint %}



