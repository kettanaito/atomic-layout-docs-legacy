# Responsive layout

## Introduction

There are two key points when creating a responsive layout:

1. Conditional areas rendering,
2. Conditional props assignment \(`gutter`, `margin`, etc.\).

## Responsive areas

### Declaration

Any grid area that is not present in all template declarations automatically becomes responsive.

```jsx
const templateMobile = `
    thumbnail
    heading
    subheading
`

const templateDesktop = `
    thumbnail heading
    thumbnail subheading
    thumbnail meta
`
```

We have two template declarations above—one for mobile and one for desktop screens. Areas `thumbnail`, `heading` and `subheading` are present in both template declarations. However, the `meta`  area is declared in `templateDesktop` only. This makes `meta` a responsive area.

{% hint style="info" %}
Note that template declaration alone has no effect over responsive area rendering. Make sure to supply the template declaration to the respective template prop.
{% endhint %}

### Breakpoints

Having different areas in different template declarations only signifies conditional areas. In order to control the breakpoints where those areas must be rendered, we need to pass templates declarations to the `template` props of the `Composition` component:

```jsx
import React from 'react'
import { Composition } from 'atomic-layout'

const templateMobile = `
    thumbnail
    heading
    subheading
`

const templateDesktop = `
    thumbnail heading
    thumbnail subheading
    thumbnail meta
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

The composition above will wrap `Meta` grid area in a `<MediaQuery/>` component from [react-responsive](https://github.com/contra/react-responsive). This area will render on `lg` breakpoint and up, because there is no succeeding template declaration that would contradict that, and because "up" is the default responsive behavior.

## Responsive props

Any prop name suffixed with a breakpoint name is a responsive prop. It implies that the prop's value will be applied on the given breakpoint.

{% hint style="info" %}
Read a more in-depth explanation about [Responsive props](../../fundamentals/responsive-props.md).
{% endhint %}

We have already used a responsive prop in the example above. By suffixing `template` with the `Lg`, we stated that the given value must be applied on the `lg` breakpoint and up. Following this example, let's create a different gutter between the grid areas on different breakpoints:

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



