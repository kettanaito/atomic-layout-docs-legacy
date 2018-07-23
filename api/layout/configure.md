---
description: Applies global layout configuration.
---

# configure\(\)

## Acknowledgement

{% hint style="danger" %}
Layout is meant to be configured **only once**, on the root level of your application.
{% endhint %}

## Options

### `defaultUnit`

| Type | `String` |
| --- | --- | --- |
| Default value | `px` |
| Description | Default measurement unit used as a suffix for numeric prop values. |

#### Example

```jsx
import Layout, { Composition } from 'atomic-layout'

Layout.configure({
    defaultUnit: 'rem',
})

<Composition gutter={2} /> // reads as "2rem" of "gutter"
```

### `defaultBehavior`

| Type | `up | down | only` |
| --- | --- | --- |
| Default value | `up` |
| Description | Breakpoint behavior used for responsive props without explicit behavior. |

#### Example

```jsx
import Layout, { Composition } from 'atomic-layout'

Layout.configure({
    defaultBehavior: 'down',
})

<Composition
    template={...}
    templateMd={...} />
```

Template prop value is applied for `md` breakpoint and _down_, as contrary to the default, mobile-first behavior, which applies the value from the given breakpoint and _up_.

### `breakpoints`

A set of [breakpoints](../../fundamentals/breakpoints.md) used in the layout composition.

| Type | `TBreakpoints` |
| --- | --- | --- |
| Default value | Bootstrap 4 breakpoints |
| Description | Map of custom breakpoints. |

#### Type definition

```typescript
type TBreakpoint = {
    minHeight?: number,
    maxHeight?: number,
    minWidth?: number,
    maxWidth?: number,
    minResolution?: string,
    maxResolution?: string,
    aspectRatio?: string,
    minAspectRatio?: string,
    maxAspectRatio?: string,
    scan?: 'interlace' | 'progressive',
    orientation?: 'portrait' | 'landscape',
    displayMode?: 'fullscreen' | 'standalone' | 'minimal-ui' | 'browser',
}

type TBreakpoints = {
    [breakpointName: string]: TBreakpoint,
}
```

#### Example

```jsx
import Layout, { Composition } from 'atomic-layout'

Layout.configure({
    breakpoints: {
        mobile: {
            maxWidth: 500,
        },
        tablet: {
            minWidth: 501,
            maxWidth: 764,
        },
        retina: {
            minResolution: '300dpi',
        },
    },
})

<Composition
    templateMobile={...}
    templateTablet={...}
    paddingRetina={10} />
```

### `defaultBreakpointName`

| Type | `String` |
| --- | --- | --- |
| Default value | `"xs"` |
| Description | The name of a default breakpoint used for the props without an explicit breakpoint name. |

#### Example

```jsx
import Layout, { Composition } from 'atomic-layout'

Layout.configure({
    defaultBreakpointName: 'mobile',
    breakpoints: {
        mobile: {
            maxWidth: 576,
        },
        desktop: {
            minWidth: 768,
        },
    },
})

<Composition
    template={...}
    templateDesktop={...} />
```

Breakpoint-less template prop references `mobile` breakpoint, as specified by `defaultBreakpointName`.

