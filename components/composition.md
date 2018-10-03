# Composition

## Specification

Composition is a base component that represents any layout composition.

## Props

Composition always expects **at least one** template string, and any [additional props](../fundamentals/prop-aliases.md).

| Prop name | Type | Description |
| :--- | :--- | :--- |
| `inline` | `boolean` | Renders composition with `display: inline-grid`. |

{% hint style="success" %}
Composition supports all [Prop aliases](../fundamentals/prop-aliases.md).
{% endhint %}

## Usage

### Import the component

First, import the `Composition` component from the library:

```jsx
import { Composition } from 'atomic-layout'
```

### Define template strings

Composition begins by defining a template string that consists of layout \(grid\) areas.

```jsx
const templateMobile = `
    logo
    menu
`
```

Template string uses [`grid-template-areas`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-areas) syntax of CSS Grid, and visually represents the layout areas.

Since Atomic layout comes with responsive behavior built-in, you can define multiple layout templates for a single composition based on the [breakpoints](../fundamentals/breakpoints.md) of your layout.

```jsx
const templateTablet = `
    logo menu
    search search
`
```

### Render Composition

Once layout templates are defined, pass them as the respective `template` props of the Composition. Each area in the template is turned into a React component and being exposed as an argument property of the children function:

```jsx
<Composition
    template={templateMobile}
    templateMd={templateTablet}>
    {({ Logo, Search, Menu }) => (
        <React.Fragment>
            <Logo>...</Logo>
            <Search>...</Search>
            <Menu>...</Menu>
        </React.Fragment>
    )}
</Composition>
```

> Area components are exposed as unique and capitalized keys based on your template definitions.

## Configuration

Composition is meant to be configurable. There is a set of [Prop aliases](../fundamentals/prop-aliases.md) you can apply to make composition suit your needs. For example, we can specify a `templateCols` prop to control the behavior of our columns on different breakpoints:

```jsx
<Composition
    template={templateMobile}
    templateMd={templateTablet}
    templateCols="1fr auto"
    templateColsMd="1fr 1fr" />
```

## Examples

### Simple composition

{% code-tabs %}
{% code-tabs-item title="src/components/ArtistCard/index.jsx" %}
```jsx
import React from 'react'
import { Composition } from 'atomic-layout'

const mobileTemplate = `
    thumbnail
    heading
    content
`

const desktopTemplate = `
    thumbnail heading
    thumbnail content
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
    thumbnail
    content
`

const desktopTemplate = `
    thumbnail content
    thumbnail content
`

const ArtistCard = ({
    title,
    description,
    publishDate,
    imageUrl,
    onShareClick
}) => (
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
                        onShareClick={onShareClick} />
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
    meta
    actions
    text
`

const desktopTemplate = `
    meta actions
    text text
`

const ArtistContent = ({ description, publishDate, onShareClick }) => (
    <Composition
        template={mobileTemplate}
        templateMd={desktopTemplate}
        gutter="10"
        gutterMd="15">
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



