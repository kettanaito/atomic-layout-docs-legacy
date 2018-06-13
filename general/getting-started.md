# Getting started

## Pre-requisites

Please make sure you have the following peer dependencies installed in your project:

* [React](https://github.com/facebook/react) \(15.0+\)
* [styled-components](https://github.com/styled-components/styled-components) \(3.0+\)

{% hint style="info" %}
Although Atomic layout is a paradigm, the current implementation uses the aforementioned  dependencies. Submit a [Pull request](https://github.com/kettanaito/atomic-layout/pulls) to bring Atomic layout to your favorite environment.
{% endhint %}

## Install

```bash
npm install atomic-layout --save
```

## Use

```jsx
import React from 'react'
// include the library
import { Layout } from 'atomic-layout'
import CardThumbnail from './CardThumbnail'
import CardContent from './CardContent'
import CardFooter form './CartFooter'

// declare layouts for different breakpoints
const mobileLayout = `
    'thumbnail'
    'content'
    'footer'
`

const tabletLayout = `
    'thumbnail content'
    'thumbnail footer'
`

const Card = ({ image, text, actions }) => (
    <Layout
        template={mobileLayout}
        gutter={1}
        templateMd={tabletLayout}
        gutterMd={2}>
        // Access all layout areas as React components
        {({ Thumbnail, Content, Footer }) => (
            <React.Fragment>
                // Treat them like non-contextual areas
                <Thumbnail rowMd="span 2">
                    // Render what's intended
                    <CartThumbnail image={image} />
                </Thumbnail>
                <Content>
                    <CardContent text={text} />
                </Content>
                <Footer>
                    <CardFooter actions={actions} />
                </Footer>
            </React.Fragment>
        )}
    </Layout>
)

export default Card
```

{% hint style="info" %}
Note that you can **nest** another compositions inside those grid areas \(`<Thumbnail/>`, `<Content/>`, `<Footer/>`\) to create astonishing layouts.
{% endhint %}

## Materials

* [Configure the layout](../api/layout/configure.md) to create powerful developer and user experience,
* Read more on Components to know how to handle your use case,
* Learn how to create truly responsive layouts with [Responsive props](responsive-props.md),
* See [Best practices](best-practices.md) to bring your layouts to the next level.



