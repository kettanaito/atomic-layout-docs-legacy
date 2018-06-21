# Breakpoints

## Breakpoint

> Breakpoint is a condition that describes a breaking point of layout acquiring next state.

You can use the following properties to describe a breakpoint in Atomic layout:

| **Property name** | **Value type** | **Description** |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| minWidth | Numeric | Minimum device width. |
| maxWidth | Numeric | Maximum device width. |
| minHeight | Numeric | Minimum device height. |
| maxHeight | Numeric | Maximum device height. |
| minResolution | String | Minimum screen resolution of the device. |
| maxResolution | String | Maximum screen resolution of the device. |
| aspectRatio | String | Device screen aspect ratio. |
| minAspectRatio | String | Minimum aspect ratio of the device. |
| maxAspectRatio | String | Maximum aspect ratio of the device. |
| scan | enum: `interlace` \| `progressive` | Scanning process of the device. |
| orientation | enum: `portrait` \| `landscape` | Device viewport orientation. |
| displayMode | enum: `fullscreen` \| `standalone` \| `minimal-ui` \| `browser` | Display mode of the application specified in the `manifest.json` |

## Default breakpoints

We are using [Bootstrap 4 Grid breakpoints](https://getbootstrap.com/docs/4.0/layout/grid/#grid-options) as default breakpoints:

| **Breakpoint name** | **xs \(default\)** | **sm** | **md** | **lg** | **xl** |
| --- | --- |
| **Screen size** | &lt;576px | ≥576px | ≥768px | ≥992px | ≥1200px |

## Custom breakpoints

You can [configure custom breakpoints](../api/layout/configure.md#breakpoints) suitable for your requirements. See the API documentation for more information and examples.

