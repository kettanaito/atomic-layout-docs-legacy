# Composition

## Specification

Component that represents a layout composition.

## Props

Composition inherits from [Box](box.md) component, thus is accepts the same props and CSS Grid props on top.

| Prop name | Type | Description |
| :--- | :--- | :--- |
| `inline` | `boolean` | Renders composition with `display: inline-grid`. |

{% hint style="info" %}
Composition supports all [Prop aliases](../fundamentals/prop-aliases.md).
{% endhint %}

## Usage

### Import the component

```jsx
import { Composition } from 'atomic-layout'
```

### Define templates

Composition begins by defining a template string that consists of layout \(grid\) areas.

```jsx
const templateMobile = `
  logo
  menu
`
```

{% hint style="info" %}
Template string is just an alias for [`grid-template-areas`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-areas).
{% endhint %}

Since Atomic layout comes with responsive built-in, you can define multiple layout templates for a single composition based on the [breakpoints](../fundamentals/breakpoints.md) of your layout.

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
    <>
      <Logo>...</Logo>
      <Search>...</Search>
      <Menu>...</Menu>
    </>
  )}
</Composition>
```

{% hint style="success" %}
Generated area components are exposed as unique capitalized keys of the children function.
{% endhint %}

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
      <>
        <Thumbnail>
          <img src={imageUrl} alt={title} />
        </Thumbail>
        <Heading>
          <h3>{title}</h3>
        </Heading>
        <Content>
          <p>{description}</p>
        </Content>
      </>
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
      <>
        <Thumbnail>
          <img src={imageUrl} alt={title} />
        </Thumbnail>
        <Content>
          <ArtistContent
            description={description}
            publishDate={publishDate}
            onShareClick={onShareClick} />
        </Content>
      </>
    )}
  </Composition>
)

export default ArtistCard
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
      <>
        <Meta>
          {publishDate}
        </Meta>
        <Actions>
          <button onClick={onShareClick}>Share</button>
        </Actions>
        <Text>
          {description}
        </Text>
      </>
    )}
  </Composition>
)

export default ArtistContent
```
{% endcode-tabs-item %}
{% endcode-tabs %}



