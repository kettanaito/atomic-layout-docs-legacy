# Workflow

## Foreword

Atomic layout is based on CSS Grid. Please make yourself comfortable at that topic to eliminate most of the questions and make your experience superb. You don't have to be an expert, but having a basic knowledge on how CSS Grid works will help you to get more from Atomic layout.

{% hint style="info" %}
We recommend reading through the [Complete guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid).
{% endhint %}

## Introduction

The biggest difference when working with Atomic layout is that you declare what your layout suppose to look like, without explicitly telling how to achieve that.

## Creating a composition

### Import

Start from importing a `Composition` component from the `atomic-layout` package:

```jsx
// ES6+
import { Composition } from 'atomic-layout'

// CommonJS
const Composition = require('atomic-layout').Composition
```

### Define layout areas

The next step is to think of what layout areas current composition acquires.

```jsx
import React from 'react'
import { Composition } from 'atomic-layout'

// grid areas on mobile devices
const templateMobile = `
    header
    content
    footer
`

// grid areas on tablets
const templateTablet = `
    header header
    content aside
    footer footer
`
```

{% hint style="info" %}
Use `grid-template-areas` syntax when declaring grid areas. Notice the explicit single quotes wrapping each line.
{% endhint %}

### Configure `Composition`

Areas declaration alone will not do anything, we need to pass those areas as a value of the `template` prop of our `Composition` component:

```jsx
import React from 'react'
import { Composition } from 'atomic-layout'

// grid areas on mobile devices
const templateMobile = `
    header
    content
    footer
`

// grid areas on tablets
const templateTablet = `
    header header
    content aside
    footer footer
`

const Page = () => (
    <Composition
        template={templateMobile}
        templateMd={templateTablet}>
        {() => (/* See next step */)}
    </Composition>
)

export default Page
```

Notice how we appended an `md` suffix in `templateMd`. `md` there refers to a breakpoint name, and having it as a suffix if any prop giving to `Composition` tells it to apply the value at that breakpoint. That is a feature called [Responsive props](../../fundamentals/responsive-props.md).

### Render layout areas

`Composition` component expects a function as its children. That function exposes areas components based on the given `template` values.

```jsx
import React from 'react'
import { Composition } from 'atomic-layout'

// grid areas on mobile devices
const templateMobile = `
    header
    content
    footer
`

// grid areas on tablets
const templateTablet = `
    header header
    content aside
    footer footer
`

const Page = () => (
    <Composition
        template={templateMobile}
        templateMd={templateTablet}
    >
        {({ Header, Content, Aside, Footer }) => (
            <React.Fragment>
                <Header>Header</Header>
                <Content>Content</Content>
                <Aside>Aside</Aside>
                <Footer>Footer</Footer>
            </React.Fragment>
        )}
    </Composition>
)

export default Page
```

{% hint style="info" %}
Notice that the Aside area exists only in templateTablet declaration. Atomic layout will automatically wrap it in a proper `<MediaQuery/>` component to prevent it from rendering on mobile devices. **Responsive grid areas are built-in**.
{% endhint %}

That's it. We have created a layout composition for our `Page` component, that consist of four layout areas. No we can render another compositions inside those layout areas, thus making a [Nested composition](../../components/composition.md#nested-composition). The latter is a main distinctive key of Atomic layout, which allows to create immersive layouts following the same pattern.

