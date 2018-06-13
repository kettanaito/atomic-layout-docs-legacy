---
description: A single component to distribute spacial relation in your layouts.
---

# Atomic layout

## Introduction

[Atomic layout](https://github.com/kettanaito/atomic-layout) is an implementational paradigm that delegates the spacial relation between any composites to the dedicated layer \(_layout layer_\).

## Motivation

Think of how you create layouts today. You most likely have a set of reusable units \(atoms\) so you can combine them into functional compositions. Units are simple and predictable, but once they become composites for layouts they acquire contextual spacing and positioning. So you apply additional CSS rules to them to ensure that behavior. That makes units **contextual**, thus not predictable \(and also makes you write more CSS, nobody likes that\).

Atomic layout exposes you a separate layer responsible for the spacial distribution between layout composites. In plain words, it allows you to set spacing and position of layout units **without mutating them**. That deprives from writing redundant CSS and ensures units being predictable.

{% page-ref page="general/philosophy.md" %}

## Advantages

* Standardized, trusted, production-ready,
* Build insanely flexible layouts via CSS Grid,
* Decrease CSS boilerplate with [Responsive props](general/responsive-props.md),
* Keep your composites immutable,
* **Just 5.6 Kb gzipped!**

## Disadvantages

* No IE support prior to version 11 \(See [CSS Grid support table](https://caniuse.com/#feat=css-grid)\)

## How does it work?

Atomic layout is based on standardized [CSS Grid](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout) feature. During the layout composition you define which layout areas are present at the given screen size\(s\) and render your components in those areas.
