# Getting started

## Use

```jsx
import React from 'react'
// include the library
import { Composition } from 'atomic-layout'
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
    <Composition
        template={mobileLayout}
        templateMd={tabletLayout}
        gutter={1}
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
    </Composition>
)

export default Card
```

{% hint style="info" %}
We encourage [Nested composition](../../components/composition.md#nested-composition) to create astonishing layouts.
{% endhint %}

## Materials

* [Configure the layout](../../api/layout/configure.md) to create powerful developer and user experience,
* Read more on Components to know how to handle your use case,
* Learn how to create truly responsive layouts with [Responsive props](../../fundamentals/responsive-props.md),
* See [Best practices](../recipes/) to bring your layouts to the next level.



