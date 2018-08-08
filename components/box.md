# Box

## Specification

Box is a primitive component responsible for spacial distribution.

{% hint style="warning" %}
Box has no control over composition. Use [Composition](composition.md) component instead.
{% endhint %}

## Props

Supports all [Prop aliases](../fundamentals/prop-aliases.md), **except** the grid-specific ones.

## Example

```jsx
import { Box } from 'atomic-layout'

const Header = () => (
    <Box paddingVertical={1} paddingVerticalMd={2}>
        <Children />
    </Box>
)

export default Header
```



