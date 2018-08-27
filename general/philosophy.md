# Philosophy

Atomic layout is heavily influenced by Atomic design, attempting to bring its principles closer to the development world in a standardized and simple form.

{% hint style="info" %}
If you are unfamiliar with [Atomic design](http://bradfrost.com/blog/post/atomic-web-design), take a minute to read through it. Thank us later.
{% endhint %}

## Motivation

The goal of Atomic layout is to introduce a dedicated layer that controls spacial relation between its children components. That helps to shift the mindset during a layout development toward focusing on the composition instead of tweaking positional/spacial properties of individual components.

## Composition

Bootstrap and Atomic layout serve a different purpose. However, comparing them makes the best visual representation of their differences, helping you understand what Atomic layout really is.

### Bootstrap

In Bootstrap you used to have a grid system that sits on top of your page and serves as a ruler you can snap to. Once the amount of grid columns is specified, you start placing some components relatively to those columns.

![Bootstrap grid visualization.](../.gitbook/assets/bootstrap-grid%20%283%29.png)

Unfortunately, that kind of grid cannot be applied down to each component you render, so you end up writing additional CSS rules for positioning and spacing of your components and their children.

### Atomic layout

Atomic layout encourages **nested** **composition**. That implies that any layout component can be a composition _and_ a composite at the same time. Think of it like a Bootstrap grid that can be applied all the way down, even to the farthest leaves of your layout.

![Atomic layout visualization.](../.gitbook/assets/atomic-layout%20%282%29.png)

This allows to have a gris system as well, as grid is but a composition of columns. However, with this approach it will rather _complement_ the composition, instead of supervising it.

