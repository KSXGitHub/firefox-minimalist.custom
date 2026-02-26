# minimal_text_fields.css

**Source:** [MrOtherGuy/firefox-csshacks](https://github.com/MrOtherGuy/firefox-csshacks/tree/master/chrome/minimal_text_fields.css) — Mozilla Public License v. 2.0

Makes the URL bar and the search bar visually minimal by removing their backgrounds and borders, and fading out most of their inner controls until the user hovers or focuses them.

## CSS Variables

| Variable | Declared on | Purpose |
|----------|-------------|---------|
| `--toolbar-field-background-color` | `:root:not([customizing])` | Set to `transparent` so the URL bar and search bar have no background by default. |
| `--toolbar-field-border-color` | `:root:not([customizing])` | Set to `transparent` to remove the border around text fields. |

## CSS Rules

| Selector | Purpose |
|----------|---------|
| `:root:not([customizing])` | Declares `--toolbar-field-background-color` and `--toolbar-field-border-color` as `transparent` when the browser is not in customization mode, making fields invisible against the toolbar background. |
| `#urlbar[open]` | Restores `--toolbar-bgcolor` as the URL bar background when its dropdown panel is open so the dropdown has a solid backdrop. |
| `#urlbar`, `#searchbar`, `#search-box` | Removes the native OS appearance, applies the transparent background color, and inherits the text color from the toolbar. |
| `#searchbar`, `#urlbar`, `.searchbar-textbox` | Removes the `box-shadow` from all text fields for a flat appearance. |
| `#tracking-protection-icon-container`, `:where(#identity-box) ~ *`, `.searchbar-textbox > *` | Fades all controls inside the URL bar and search bar to `opacity: 0` by default, with a `150ms` linear transition, so they only appear when needed. |
| `.urlbar-input-container > :is(.urlbar-searchmode-and-input-box-container, .urlbar-input-box)`, `.searchbar-textbox > moz-input-box` | Keeps the actual text input area at `opacity: 0.6` so the user can see what they are typing even when the bar is not focused. |
| `#identity-box ~ *:hover`, `#tracking-protection-icon-container:hover`, `#tracking-protection-icon-container ~ *:hover`, `#urlbar:focus-within > *`, `.urlbar-input-container:focus-within > *`, `.searchbar-textbox:hover > *`, `.searchbar-textbox:focus-within > *` | Reveals all controls (`opacity: 1`) when the URL bar is focused or hovered, or when any of its inner icons is hovered. |
| `#identity-box` | Removes the border around the site-identity button. |
| `#urlbar:not(:hover) #identity-box` | Shows a small orange radial-gradient dot (a subtle security indicator) behind the site-identity icon when the bar is not hovered. |
| `#urlbar:not(:hover) #identity-box.verifiedIdentity` | Changes the dot to lime green for EV (extended-validation) HTTPS sites when the bar is not hovered. |
| `#urlbar:not(:hover) #identity-box > *` | Hides all children of the identity box when the bar is not hovered, leaving only the colored dot visible. |
| `#urlbar[pageproxystate=invalid]:not([usertyping]) #identity-box`, `#identity-box:hover`, `#identity-box.chromeUI`, `#identity-box.verifiedDomain` | Removes the colored dot on browser-internal pages (`chromeUI`), when the user is typing, when the identity box is hovered, or for regular HTTPS domains. |
| `#identity-box > #identity-icon-labels` | Adds a `150ms` transition to the `max-width` of the identity label so it animates in smoothly. |
| `#identity-box:not(:hover) > #identity-icon-labels` | Collapses the identity label to `max-width: 0px` when the identity box is not hovered, hiding the site name text. |
