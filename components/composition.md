---
description: A component responsible for elements composition and spacial distribution.
---

# Composition

## Props

Supports all the [Responsive props](../fundamentals/responsive-props.md).

## Examples

### Simple composition

{% code-tabs %}
{% code-tabs-item title="src/components/ArtistCard/index.jsx" %}
```jsx
import React from 'react'
import { Composition } from 'atomic-layout'

const mobileTemplate = `
    'thumbnail'
    'heading'
    'content'
`

const desktopTemplate = `
    'thumbnail heading'
    'thumbnail content'
`

const ArtistCard = ({ title, imageUrl, description }) => (
    <Composition
        template={mobileTemplate}
        templateMd={desktopTemplate}
        gutter={1}
        gutterMd={2}
        padding={1}>
        {({ Thumbnail, Heading, Content }) => (
            <React.Fragment>
                <Thumbnail>
                    <img src={imageUrl} alt={title} />
                </Thumbail>
                <Heading>
                    <h3>{title}</h3>
                </Heading>
                <Content>
                    <p>{description}</p>
                </Content>
            </React.Fragment>
        )}
    </Composition>
)

export default ArtistCard
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Nested composition

{% code-tabs %}
{% code-tabs-item title="components/ArtistCard/index.jsx" %}
```jsx
import React from 'react'
import { Composition } from 'atomic-layout'
import ArtistContent from './ArtistContent'

const mobileTemplate = `
    'thumbnail'
    'content'
`

const desktopTemplate = `
    'thumbnail content'
    'thumbnail content'
`

const ArtistCard = ({ title, description, publishDate, imageUrl }) => (
    <Composition template={mobileTemplate}>
        {({ Thumbnail, Content }) => (
            <React.Fragment>
                <Thumbnail>
                    <img src={imageUrl} alt={title} />
                </Thumbnail>
                <Content>
                    <ArtistContent
                        description={description}
                        publishDate={publishDate}
                        onShareClick={() => console.log('foo')} />
                </Content>
            </React.Fragment>
        )}
    </Composition>
)

export default Foo
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="components/ArtistCard/ArtistContent.jsx" %}
```jsx
import React from 'react'
import { Composition } from 'atomic-layout'

const mobileTemplate = `
    'meta'
    'actions'
    'text'
`

const desktopTemplate = `
    'meta actions'
    'text text'
`

const ArtistContent = ({ description, publishDate, onShareClick }) => (
    <Composition
        template={mobileTemplate}
        templateMd={desktopTemplate}
        gutter={1}
        gutterMd={1.5}>
        {({ Meta, Actions, Text }) => (
            <React.Fragment>
                <Meta>
                    {publishDate}
                </Meta>
                <Actions>
                    <button onClick={onShareClick}>Share</button>
                </Actions>
                <Text>
                    {description}
                </Text>
            </React.Fragment>
        )}
    </Composition>
)

export default ArtistContent
```
{% endcode-tabs-item %}
{% endcode-tabs %}



