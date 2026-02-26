# navbar_tabs_responsive_oneliner.css

**Source:** [MrOtherGuy/firefox-csshacks](https://github.com/MrOtherGuy/firefox-csshacks/tree/master/chrome/navbar_tabs_responsive_oneliner.css) — Mozilla Public License v. 2.0

Merges the navigation bar and the tab strip into a single horizontal row (tabs on the right, address bar on the left) on wide screens. When the window is narrower than `1100px` the toolbars fall back to their default stacked layout.

## CSS Variables

These variables are declared on `#navigator-toolbox` and control the layout of the one-liner:

| Variable | Default | Purpose |
|----------|---------|---------|
| `--uc-navigationbar-width` | `40vw` | Width of the navigation bar column. The tab strip fills the remaining space to the right. |
| `--uc-toolbar-height` | `40px` | Height of the combined toolbar row. Overridden to `34px` for compact density and `44px` for touch density. |
| `--uc-urlbar-min-width` | `50vw` | Minimum width the URL bar expands to when its dropdown is open. |
| `--uc-window-drag-space-width` | `24px` | Width of the empty drag area added to the left of the nav-bar in non-maximized windowed mode (declared on `:root[tabsintitlebar][sizemode="normal"]`). |

## CSS Rules

All rules below are wrapped in `@media screen and (min-width: 1100px)` unless otherwise noted.

| Selector | Purpose |
|----------|---------|
| `:root[tabsintitlebar][sizemode="normal"]` | Declares `--uc-window-drag-space-width: 24px` for the window drag area. |
| `:root[uidensity="compact"]` | Sets `--tab-block-margin: 2px` inside the media query for compact density. |
| `#navigator-toolbox` | Declares `--uc-navigationbar-width`, `--uc-toolbar-height`, and `--uc-urlbar-min-width`. |
| `#scrollbutton-up`, `#scrollbutton-down` | Sets a `2px` block border on the tab-strip scroll buttons so they align correctly in the one-liner layout. |
| `@media screen and (max-width: 1500px) #urlbar-container` | Prevents the URL bar from overflowing on narrower-but-still-wide windows by setting a `300px` minimum width and allowing it to shrink. |
| `:root[uidensity="compact"] #navigator-toolbox` | Overrides `--uc-toolbar-height` to `34px` for compact density. |
| `:root[uidensity="touch"] #navigator-toolbox` | Overrides `--uc-toolbar-height` to `44px` for touch density. |
| `#TabsToolbar` | Pushes the tab strip to the right by applying a left margin equal to `--uc-navigationbar-width`, and removes its bottom shadow. |
| `#tabbrowser-tabs` | Sets `--tab-min-height` to `--uc-toolbar-height` minus twice `--tab-block-margin` so tabs fill the full one-liner height. |
| `.titlebar-spacer[type="pre-tabs"]` | Hides the pre-tab spacer because it is not meaningful when tabs start in the middle of the window. |
| `#navigator-toolbox > #nav-bar` | Pulls the nav-bar up by a negative top margin equal to `--uc-toolbar-height` and limits its right margin so it only occupies `--uc-navigationbar-width`. |
| `:root[tabsintitlebar="true"] #nav-bar` | Adds left padding equal to `--uc-window-drag-space-width` for the window drag area. |
| `@media (-moz-gtk-csd-reversed-placement), (-moz-platform: macos) .titlebar-buttonbox-container` | Fixes window control buttons (minimize/maximize/close) on Linux and macOS with left-side controls by positioning them with `position: fixed` at the left edge and centering them vertically within the toolbar. |
| `@media (-moz-gtk-csd-reversed-placement), (-moz-platform: macos) :root[tabsintitlebar="true"] #nav-bar` | Adds extra left padding (drag space + `84px`) on Linux with reversed window controls to accommodate the control buttons. |
| `@media (-moz-platform: macos) :root[tabsintitlebar="true"] #nav-bar` | Overrides the above to use `72px` (the standard macOS traffic-light button width) instead of `84px`. |
| `.tab-close-button` | Removes the top margin of the tab close button in touch density to keep it properly aligned. |
| `#urlbar[open]:focus-within` | Expands the URL bar to at least `--uc-urlbar-min-width` when its dropdown is open and the bar is focused, so the dropdown does not appear too narrow. |
| `#urlbar-container:not(:hover) .urlbar-history-dropmarker` | Shifts the URL bar history drop-marker off-screen with a negative inline-start margin when the bar is not hovered, effectively hiding it without `display: none`. |
| `#customization-panelWrapper > .panel-arrowbox > .panel-arrow` (outside media query) | Resets the inline-end margin of the customization panel arrow to its initial value, fixing a misalignment that the one-liner layout would otherwise cause. |
