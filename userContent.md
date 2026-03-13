# userContent.css.disabled

This stylesheet customizes the content pages that Firefox renders internally (the "new tab" page, blank pages, private browsing page, etc.). The file is shipped with a `.disabled` extension so it is not loaded automatically; rename it to `userContent.css` to activate it.

It imports `content/theme.css` first so that all custom color variables are available, then applies the following rules inside a `@-moz-document` block that targets `about:home`, `about:newtab`, `about:privatebrowsing`, `about:blank`, `about:logo`, and `about:robots`.

## CSS Rules

| Selector | Purpose |
|----------|---------|
| `body.activity-stream` | Sets the activity-stream new-tab background to `--uc-main-bgcolor` via both a Firefox-specific variable and the standard `background-color` property. |
| `body:empty` | Covers blank pages with `--uc-main-bgcolor` so they match the rest of the theme. |
| `.search-handoff-button` | Rounds the search bar pill, applies `--uc-panel-bgcolor` as its background, `--uc-main-color` as its text color, and `--uc-active-color` for the primary action color. |
| `.icon-settings:hover`, `.close-button:hover` | Highlights settings and close icons on hover using `--uc-hover-color`. |
| `.icon-settings:active`, `.close-button:active` | Provides active/pressed feedback using `--uc-active-color`. |
| `.customize-menu` | Colors the customization side-panel with `--uc-panel-bgcolor`. |
| `.close-button`, `.selector` | Applies `--uc-hover-selected` as background and removes borders from close buttons and selectors. |
| `.slider`, `.sponsored-checkbox` | Colors toggle sliders and sponsored-content checkboxes with `--uc-active-color`. |
| `.tile` | Applies `--uc-hover-selected` as background and a large `50px` border-radius to top-site tiles. |
| `.tile:hover`, `.weatherInfoLink:hover`, `.weatherButtonContextMenu:hover` | Highlights tiles and weather widgets on hover using `--uc-hover-color`. |
| `.top-site-icon` | Removes the background from individual site icons inside a tile so only the favicon is visible. |
| `.search-topsite` | Hides the "Search" shortcut tile that appears by default. |
| `.top-site-outer` | Removes the background from the outer top-site wrapper to avoid double backgrounds. |
| `.context-menu` | Colors the right-click context menu with `--uc-panel-bgcolor`. |
| `.context-menu > ul > li > button:is(:focus, :hover)` | Highlights focused or hovered context-menu items using `--uc-hover-selected`. |
