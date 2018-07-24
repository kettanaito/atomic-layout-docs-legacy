---
description: A primitive component responsible for spacial distribution.
---

# Box

## Props

Supports all the [Responsive props](../fundamentals/responsive-props.md), **except the grid-specific ones**.

## Example

{% code-tabs %}
{% code-tabs-item title="src/components/Header.jsx" %}
```jsx
import { Box } from 'atomic-layout'

const Header = () => (
    <Box paddingVertical={1} paddingVerticalMd={2}>
        <ChildElement />
    </Box>
)

export default Header
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="warning" %}
Box has no control over composition. Use [Composition](composition.md) component when such is needed.
{% endhint %}



