# Philosophy

## Introduction

Atomic layout is an implementational paradigm based on Atomic design, which aims to simplify and standardize any layout composition using flexible primitives.

{% hint style="info" %}
If you are unfamiliar with [Atomic design](http://bradfrost.com/blog/post/atomic-web-design), take a minute to read through it.
{% endhint %}

## Motivation

The goal of Atomic layout is to introduce a dedicated layer that controls spacial relation between its children components. That helps to shift the mindset during a layout development toward focusing on the composition instead of tweaking positional/spacial properties of individual components.

## Composition

The easiest way to describe the composition concept is using Bootstrap's grid as an example.

### Bootstrap grid

In Bootstrap you used to have a grid system that sits on top of your page and serves as a ruler you can snap to. Once you set the amount of columns in the grid, you start placing some components relatively to those columns.

![Bootstrap grid visualization.](../.gitbook/assets/bootstrap-grid%20%283%29.png)

Unfortunately, that kind of grid cannot be applied down to each component you render, so you end up writing additional CSS rules for positioning and spacing of your components and their children.

### Atomic layout

Atomic layout principle encourages **nested** **composition**. That implies that any layout part can be a composition **and** a composite at the same time. Think of it like a Bootstrap grid that can be applied all the way down, even to the farthest leaves of your layout.

![Atomic layout visualization.](../.gitbook/assets/atomic-layout%20%282%29.png)

{% hint style="info" %}
Nested composition is a core difference between Atomic layout and conventional grid systems.
{% endhint %}

You can still build containers and grids, which will _complement_ the composition instead of supervising it.

