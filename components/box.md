# Box

## Specification

Box is a primitive component responsible for spacial distribution.

{% hint style="warning" %}
Box has no control over layout composition. Use [Composition](composition.md) component instead.
{% endhint %}

## Props

Box supports all [Prop aliases](../fundamentals/prop-aliases.md), **except** those specific to CSS Grid.

## Example

```jsx
import React from 'react'
import { Box } from 'atomic-layout'

const Header = ({ children }) => (
  <Box paddingVertical="10" paddingVerticalMd="20">
    {children}
  </Box>
)

export default Header
```



