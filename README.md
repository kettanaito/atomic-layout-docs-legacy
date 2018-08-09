---
description: A single component to distribute a spacial relation in your layouts.
---

# Atomic layout

## Introduction

[Atomic layout](https://github.com/kettanaito/atomic-layout) is an implementational paradigm that delegates the spacial relation between any composites to the dedicated layout layer.

## Motivation

Think of how you create layouts today. You most likely have a set of reusable units \(atoms\) so you can combine them into functional compositions. Units are simple and predictable, but once they become composites for layouts they acquire contextual spacing and positioning. So you apply additional CSS rules to them to ensure that behavior. That makes units **contextual**, thus not predictable \(and also makes you write more CSS, nobody likes that\).

Atomic layout exposes you a separate layer responsible for the spacial distribution between layout composites. In plain words, it allows you to set spacing and position of layout units **without mutating them**. That deprives from writing redundant CSS and ensures units being predictable.

{% page-ref page="general/philosophy.md" %}

## Advantages

* Standardized, trusted, production-ready,
* Flexible layouts via CSS Grid without writing actual CSS,
* Use [Responsive props](fundamentals/responsive-props.md) to create responsive layouts in a few lines,
* Immutable layout composites,
* **~6 Kb gzipped!**

## Disadvantages

* No Internet Explorer support prior to version 11 \(See [CSS Grid support table](https://caniuse.com/#feat=css-grid)\)

## How does it work?

Atomic layout is based on the standardized [CSS Grid](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout). During the layout composition you define which layout areas are present at the desired breakpoint\(s\) and render your components in those areas.

**Learn more by going through a quick guide:**

{% page-ref page="general/getting-started/" %}

