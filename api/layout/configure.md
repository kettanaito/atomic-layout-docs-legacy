---
description: Applies global layout configuration.
---

# configure\(\)



{% hint style="danger" %}
**Configure layout once**, on the root level of your application, to ensure its consistency.
{% endhint %}

## Options

### `defaultUnit`

| Type | `String` |
| --- | --- | --- |
| Default value | `px` |
| Description | Default measurement unit used as a supplement for numeric prop values. |

#### Usage

```jsx
import Layout, { Composition } from 'atomic-layout'

Layout.configure({
    defaultUnit: 'rem'
})

<Composition gutter={2} /> // reads as "2rem" of "gutter"
```

### `breakpoints`

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

#### Usage

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
        }
    },
})

<Composition
    templateMobile={...}
    templateTablet={...}
    paddingRetina={10} />
```

