# hide_toolbox_top_bottom_borders.css

**Source:** [MrOtherGuy/firefox-csshacks](https://github.com/MrOtherGuy/firefox-csshacks/tree/master/chrome/hide_toolbox_top_bottom_borders.css) — Mozilla Public License v. 2.0

Removes the thin border lines that Firefox draws at the very top and bottom of the toolbox (`#navigator-toolbox`), giving a cleaner, edge-to-edge look.

## CSS Rules

| Selector | Purpose |
|----------|---------|
| `:root[sizemode="normal"]` | Removes the top border of the browser window in non-maximized ("normal") mode. |
| `#navigator-toolbox::after` | Suppresses the pseudo-element that renders the bottom border line below the toolbox. |
| `#navigator-toolbox` | Removes the bottom border of the toolbox itself. |
| `:root[sizemode="normal"] #titlebar` | Sets `-moz-appearance: none` on the title bar in non-maximized windows to eliminate a few extra pixels above the tab strip and prevent a small vertical shift when dragging tabs in compact density. |

> **Optional rules (commented out):** Two additional selectors are included but disabled by default. They remove the remaining space above the tabs by applying a negative top margin or hiding a spacer element. Note that these increase the effective height of tabs rather than reducing the toolbar height.
>
> - `#navigator-toolbox > #TabsToolbar { margin-top: -2px; }` — for Firefox prior to version 65.
> - `#TabsToolbar > .toolbar-items > spacer { display: none; }` — for Firefox 65 and later.
