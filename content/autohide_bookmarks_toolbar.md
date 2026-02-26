# autohide_bookmarks_toolbar.css

**Source:** [MrOtherGuy/firefox-csshacks](https://github.com/MrOtherGuy/firefox-csshacks/tree/master/chrome/autohide_bookmarks_toolbar.css) — Mozilla Public License v. 2.0

Hides the bookmarks toolbar by default and reveals it when the cursor enters the toolbar area or the URL bar is focused, using a 3-D `rotateX` CSS transform.

## CSS Variables

These variables are declared on `#PersonalToolbar` and can be adjusted to tune the behaviour:

| Variable | Default | Purpose |
|----------|---------|---------|
| `--uc-bm-height` | `20px` | Height of the bookmarks toolbar items. Increase this if the toolbar contains other (taller) buttons. |
| `--uc-bm-padding` | `4px` | Vertical padding applied to each bookmark item. |
| `--uc-autohide-toolbar-delay` | `600ms` | How long the toolbar stays visible after the trigger condition ends before hiding again. |
| `--uc-autohide-toolbar-focus-rotation` | `0deg` | Rotation angle used when the URL bar is focused. `0deg` = shown; `90deg` = hidden. |
| `--uc-autohide-toolbar-hover-rotation` | `0deg` | Rotation angle used when the cursor is over the toolbar area. `0deg` = shown; `90deg` = hidden. |

## CSS Rules

| Selector | Purpose |
|----------|---------|
| `#PersonalToolbar` | Declares the variables above on the bookmarks toolbar element. |
| `:root[uidensity="touch"] #PersonalToolbar` | Increases `--uc-bm-padding` to `7px` when touch density is active. |
| `#PersonalToolbar:not([customizing])` | Hides the toolbar by applying `rotateX(90deg)` transform and a negative bottom margin, making it invisible without affecting layout. Sets a `135ms` transition (plus the configurable delay) for a smooth reveal animation. Also reconstructs the background image stack so transparent LWT (Lightweight Theme) backgrounds continue to work correctly. |
| `@media (-moz-bool-pref: "sidebar.verticalTabs")` | Adjusts margin and background calculations when the vertical-tabs sidebar is enabled. |
| `:root[uidensity="compact"] #PersonalToolbar` | Forces `--toolbarbutton-outer-padding` to `1px` in compact density. |
| `#PlacesToolbarItems > .bookmark-item`, `#OtherBookmarks`, `#PersonalToolbar > #import-button` | Applies the `--uc-bm-padding` padding to individual bookmark items and the "Other Bookmarks" / "Import" buttons. |
| `#nav-bar:focus-within + #PersonalToolbar` | Shows the toolbar (reduces transition delay to `100ms`) when the URL bar or another element inside the nav-bar gains focus. |
| `#navigator-toolbox:is(:hover,:focus-within)` | Hides the bottom border of the toolbox while it is hovered or focused to avoid a visual artefact. |
| `#navigator-toolbox:hover > #PersonalToolbar` | Shows the toolbar on hover using `--uc-autohide-toolbar-hover-rotation`. |
| `#navigator-toolbox:hover > #nav-bar:focus-within + #PersonalToolbar` | Ensures the toolbar is fully shown (`rotateX(0)`) when both the toolbox is hovered and the nav-bar is focused simultaneously. |
| `#navigator-toolbox` | Sets `--browser-area-z-index-toolbox` to `4` so the revealed toolbar renders above page content. |
