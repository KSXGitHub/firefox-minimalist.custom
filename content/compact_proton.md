# compact_proton.css

**Source:** [MrOtherGuy/firefox-csshacks](https://github.com/MrOtherGuy/firefox-csshacks/tree/master/chrome/compact_proton.css) — Mozilla Public License v. 2.0

Makes the Proton UI design (introduced in Firefox 89) roughly as compact as the older "compact" density mode by tightening toolbar button padding, tab margins, panel font size, and several other spacing values.

## CSS Variables

These variables are declared on `:root` and override Firefox's built-in defaults:

| Variable | Value | Purpose |
|----------|-------|---------|
| `--toolbarbutton-inner-padding` | `6px` | Reduces the padding inside toolbar buttons. |
| `--tab-block-margin` | `2px` | Reduces the vertical margin around tabs. |
| `--tabs-shadow-size` | `0px` | Removes the shadow that separates the tab bar from the navigation bar. |
| `--arrowpanel-menuitem-padding-block` | `5px` | Reduces top/bottom padding of menu items inside arrow panels. |
| `--panel-font-size` | `inherit` | Prevents panels from using a larger-than-page font size. |
| `--arrowpanel-padding` | `0.8em` | Reduces the padding inside arrow panels. |
| `--inline-tab-padding` | `8px` | Controls horizontal padding inside tabs (default value kept; lower values compress tabs further). |
| `--tab-inline-padding` | `8px` | Same purpose as `--inline-tab-padding`, used in Firefox 132+. |
| `--uc-tabs-scrollbutton-border` | `2px` | Controls the block border width of the tab scroll buttons (declared on `#tabbrowser-tabs`). |

## CSS Rules

| Selector | Purpose |
|----------|---------|
| `:root` | Declares all the compacting CSS variables listed above. |
| `.subviewbutton.bookmark-item` | Reduces block padding of bookmark items in subview panels to `4px`. |
| `.subview-subheader` | Ensures subview section headers are rendered as `block` elements (they may be hidden by default). |
| `menupopup > menuitem`, `menupopup > menu` | Reduces block padding of menu items in popup menus to `0.3em`. |
| `#nav-bar` | Applies an inset `box-shadow` equal to `--tabs-shadow-size` using `--lwt-tabs-border-color`, rendering the tab/nav-bar separator line "inside" the nav-bar rather than between the two bars for a tighter look. |
| `.tab-close-button` | Sets the close button to `20×20 px` with `5px` internal padding and removes the default inline-start margin. |
| `#tabbrowser-tabs` | Declares `--uc-tabs-scrollbutton-border: 2px` to control scroll-button borders. |
| `#scrollbutton-up`, `#scrollbutton-down` | Applies `--uc-tabs-scrollbutton-border` as the block border width on the tab-strip scroll buttons. |
