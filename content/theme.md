# theme.css

Defines the color palette for the entire Firefox-Minimalist theme and applies it to every part of the Firefox UI. This file is imported by both `userChrome.css` and `userContent.css.disabled` so the same colors are used for both chrome and content pages.

## CSS Color Variables

The palette is declared on `:root` as a set of `--uc-*` custom properties:

| Variable | Value | Purpose |
|----------|-------|---------|
| `--uc-main-bgcolor` | `#21252b` | Darkest background — used for the toolbar, tab bar, and main browser area. |
| `--uc-bgcolor` | `#282c34` | Secondary background — used for input fields and edit-bookmark panel elements. |
| `--uc-active-color` | `#0063b1` | Blue accent color — used for active/selected states (selected tab, pressed buttons, active URL bar row). |
| `--uc-hover-color` | `#33466c` | Mid-blue — used for hover states on toolbar buttons, URL bar icons, and context-menu navigation items. |
| `--uc-hover-selected` | `#2c313c` | Subtle dark blue-grey — used for hover states on rows, subview buttons, and tab close buttons. |
| `--uc-panel-bgcolor` | `#353b45` | Panel background — used for drop-down panels, popup menus, and side panels. |
| `--uc-main-color` | `#fff` | Primary text and icon color. |
| `--uc-separator-color` | `#494e57` | Color for separator lines inside panels. |

## Firefox Built-in Variable Overrides

A second `:root` block maps the custom palette to Firefox's built-in CSS variables so that native UI elements automatically pick up the theme colors:

| Firefox Variable | Mapped to | Purpose |
|-----------------|-----------|---------|
| `--toolbar-bgcolor` | `--uc-main-bgcolor` | Toolbar background. |
| `--toolbar-field-focus-border-color` | `--uc-hover-color` | Border color of the URL bar when focused. |
| `--toolbar-field-focus-background-color` | `--uc-panel-bgcolor` | Background of the URL bar when focused. |
| `--toolbar-field-hover-background-color` | `--uc-hover-selected` | Background of the URL bar on hover. |
| `--toolbarbutton-active-background` | `--uc-active-color` | Background of a toolbar button when pressed. |
| `--toolbarbutton-hover-background` | `--uc-hover-color` | Background of a toolbar button on hover. |
| `--arrowpanel-color` | `--uc-main-color` | Text color inside arrow panels. |
| `--arrowpanel-background` | `--uc-panel-bgcolor` | Background color inside arrow panels. |
| `--lwt-text-color` | `--uc-main-color` | Text color for LWT (Lightweight Theme) elements. |
| `--toolbar-non-lwt-textcolor` | `--uc-main-bgcolor` | Text color in toolbars without an LWT. |
| `--button-hover-bgcolor` | `transparent` | Removes the default background on button hover (handled by `--toolbarbutton-hover-background`). |
| `--panel-separator-color` | `--uc-separator-color` | Color of separator lines in panels. |
| `--tab-block-margin` | `none` | Removes the default block margin between tabs (overridden later). |
| `--tabpanel-background-color` | `--uc-main-color` | Background color of the tab panel (page content area). |
| `--urlbarView-separator-color` | `none` | Removes separator lines in the URL bar dropdown. |

## Layout & Sizing Variables

A third `:root` block defines layout variables:

| Variable | Value | Purpose |
|----------|-------|---------|
| `--uc-border-radius` | `4px` | Rounded-corner radius used throughout the theme. |
| `--uc-height` | `30px` | Uniform height for the toolbar, URL bar, tabs, and related elements. |
| `--tab-overflow-clip-margin` | `0px` | Removes the spacing between tabs. |
| `--tab-block-margin` | `-2px` | Negative margin to tighten vertical tab spacing. |
| `--urlbar-min-height` | `30px` | Minimum height of the URL bar. |
| `--tab-min-height` | `30px` | Minimum tab height. |
| `--tab-max-height` | `30px` | Maximum tab height. |

## Overrides for navbar_tabs_responsive_oneliner.css

Applied inside `@media screen and (min-width: 1100px)`:

| Selector | Purpose |
|----------|---------|
| `#navigator-toolbox` | Sets `--uc-urlbar-min-width: 20vw` and `--uc-toolbar-height` to `--uc-height` for the one-liner layout at wide viewport widths. |

## Overrides for autohide_bookmarks_toolbar.css

| Selector | Purpose |
|----------|---------|
| `#PersonalToolbar` | Sets `--toolbar-bgcolor` to `--uc-main-bgcolor` so the revealed bookmarks toolbar matches the rest of the UI. Sets `--uc-autohide-toolbar-focus-rotation: 90deg` to keep the toolbar hidden even when the URL bar is focused. |

## Responsive Media Queries

| Breakpoint | Selector | Purpose |
|------------|----------|---------|
| `max-width: 1340px` | `#unified-extensions-button` | Hides the unified extensions button on narrower screens to save toolbar space. |
| `max-width: 1340px` | `#nav-bar-overflow-button` | Hides the overflow chevron button on narrower screens. |
| `max-width: 1100px` | `#nav-bar` | Sets a maximum height and a small negative bottom margin on the nav-bar to ensure it fits within the stacked layout. |
| `max-width: 1100px` | `#navigator-toolbox` | Limits the toolbox height to twice `--uc-height` and adds `1px` top margin to avoid overlap. |

## Toolbar Rules

| Selector | Purpose |
|----------|---------|
| `#titlebar`, `#nav-bar`, `toolbarbutton`, `toolbaritem`, `#urlbar-container`, `.urlbar-input-container` | Limits the maximum height of all toolbar elements to `--uc-height`. |
| `.urlbar-input-container`, `#urlbar-background`, `toolbarbutton` | Removes the top block-start margin. |
| `#PanelUI-button` | Reorders the hamburger menu button to be the leftmost toolbar item (`order: -2`) and adds `10px` left / `5px` right margin. |
| `#TabsToolbar`, `#toolbar-menubar`, `#navigator-toolbox` | Sets the background to `--uc-main-bgcolor`. |
| `.titlebar-button` | Applies `--uc-border-radius` to window control buttons (minimize, maximize, close). |
| `.titlebar-min:hover`, `.titlebar-max:hover`, `.titlebar-restore:hover`, `#urlbar-searchmode-switcher:hover` | Applies `--uc-hover-color` as the hover background for window controls and the search-mode switcher. |
| `.titlebar-min:active`, `.titlebar-max:active`, `.titlebar-restore:active` | Applies `--uc-active-color` as the active/pressed background for window controls. |
| `#urlbar-searchmode-switcher` | Sets background to `--uc-bgcolor-` (note: the source CSS contains a trailing hyphen — this is a typo for `--uc-bgcolor`; because the variable `--uc-bgcolor-` is undefined the background resolves to transparent) and adds `6px` top margin. |
| `.titlebar-button` | Sets horizontal padding to `14px` and a `0.2s` opacity transition. |
| `.toolbarbutton-1` | Removes padding from first-level toolbar buttons. |
| `.bookmark-item` | Adds `4px` margin around bookmark items. |
| `.subviewbutton:hover` | Applies `--uc-hover-selected` as the hover background for subview buttons. |
| `.titlebar-spacer[type="post-tabs"]` | Hides the post-tabs spacer that would otherwise create unused space at the right end of the tab strip. |
| `#navigator-toolbox` | Removes the border around the entire toolbox. |

## Tab Rules

| Selector | Purpose |
|----------|---------|
| `.tabbrowser-tab`, `#TabsToolbar-customization-target.customization-target` | Sets tab and customization target height to `--uc-height`. |
| `.tabbrowser-tab[fadein]` | Limits tabs to a maximum width of `140px` and a minimum of `32px`. |
| `.tabbrowser-tab` | Removes all padding from tabs. |
| `.tab-background` | Sets the default (unselected) tab background to `--uc-main-bgcolor`. |
| `.tab-background[selected]` | Sets the selected tab background to `--uc-active-color`. |
| `.tabbrowser-tab:hover > .tab-stack > .tab-background:not([selected])` | Applies `--uc-hover-color` to unselected tabs on hover. |
| `.tab-close-button:hover` | Applies `--uc-hover-selected` when the tab close button is hovered. |
| `#firefox-view-button` | Hides the Firefox View button. |

## URL Bar Rules

| Selector | Purpose |
|----------|---------|
| `#urlbar-input` | Sets the URL bar input field height to `--uc-height`. |
| `#searchbar`, `#urlbar`, `.searchbar-textbox` | Applies a `-2px` top margin to fine-tune vertical alignment. |
| `.urlbarView` | Removes the autocomplete popup separator color. |
| `.urlbarView-row[selected]`, `.urlbarView-row[type="switchtab"][selected]`, `.searchbar-engine-one-off-item[selected]`, `#urlbar-search-mode-indicator` | Applies `--uc-active-color` to selected rows and the search-mode indicator in the URL bar dropdown. |
| `.urlbarView-row:hover`, `.urlbarView-row[type="switchtab"]:hover`, `#urlbar-search-mode-indicator-close:hover` | Applies `--uc-hover-selected` to hovered rows in the dropdown. |
| `.identity-box-button:hover`, `#tracking-protection-icon-container:hover`, `.urlbar-page-action:hover`, `.searchbar-engine-one-off-item:hover`, `#urlbar-go-button:hover`, `.urlbarView-row[type="switchtab"]` | Applies `--uc-hover-color` to URL bar icon buttons and "switch to tab" rows. |
| `:is(.urlbarView-row[selected],.urlbarView-row:hover) .urlbarView-row-inner` | Sets the inner row background to `invisible` (not a valid CSS value — effectively `transparent`) to prevent a double highlight inside selected/hovered rows. |
| `.search-one-offs` | Adds `6px` bottom padding to the one-off search engine buttons row. |
| `.urlbarView`, `#urlbar`, `#urlbar-background` | Applies `--uc-border-radius` to the URL bar and its dropdown panel. |
| `#urlbar-background` | Removes the outline around the URL bar background element. |

## Menu Rules

| Selector | Purpose |
|----------|---------|
| `.panel-subview-body`, `.menupopup-arrowscrollbox`, `menupopup > menuitem[_moz-menuactive="true"]` | Sets background to `--uc-panel-bgcolor` and text color to `--uc-main-color` for panel subviews and popup menus. |
| `.download-state:hover`, `menupopup > menuitem:hover`, `menupopup > menu:hover`, `menupopup > menucaption:hover` | Applies `--uc-hover-selected` and white text color to hovered menu items. |
| `#context-navigation > menuitem[_moz-menuactive] .menu-iconic-icon` | Applies `--uc-border-radius` to the icon of an active navigation context-menu item. |
| `menupopup:not(.in-menulist)` | Removes panel padding from popup menus that are not inside a list widget. |
| `menupopup` | Applies `--uc-border-radius` as the panel border radius for all popup menus. |
| `.menupopup-arrowscrollbox` | Sets `4px` top and bottom padding in the scrollable area of popup menus. |
| `#context-navigation` | Adds `4px` horizontal padding to the browser right-click navigation bar (back, forward, reload, stop, bookmark). |
| `#context-back:hover image`, `#context-forward:hover image`, `#context-reload:hover image`, `#context-stop:hover image`, `#context-bookmarkpage:hover image`, `#context-sep-navigation:hover` | Applies `--uc-hover-color` to the icons of the context-menu navigation buttons on hover. |
| `#context-sep-navigation` | Hides the separator line below the context-menu navigation buttons. |

## Other Rules

| Selector | Purpose |
|----------|---------|
| `#editBMPanel_chooseFolderSeparator`, `#editBMPanel_foldersSeparator` | Hides the separator lines inside the edit-bookmark panel. |
| `stack input`, `#editBMPanel_folderTree`, `#editBMPanel_newFolderButton`, `#editBookmarkPanelRemoveButton`, `#editBMPanel_folderMenuList`, `#editBMPanel_foldersExpander`, `#editBMPanel_tagsSelectorExpander`, `#editBMPanel_namePicker`, `#editBMPanel_tagsField` | Applies `--uc-bgcolor` as the background for all input fields and controls inside the edit-bookmark panel. |
| `.PanelUI-subView`, `#downloadsPanel-mainView`, `#password-notification`, `.popup-notification-body-container`, `#permission-popup-mainView`, `.panel-header`, `#protections-popup-mainView`, `#identity-popup-mainView`, `.tab-preview-text-container`, `.cui-widget-panelview`, `#addon-webext-permissions-notification`, `#appMenu-addon-installed-notification` | Applies `--uc-panel-bgcolor` as the background for all major panel and popup views. |
| `.unified-extensions-item-menu-button.subviewbutton` | Applies `--uc-border-radius` to the per-extension menu button. |
| `.downloadButton:hover`, `.popup-notification-dropmarker:hover`, `.popup-notification-primary-button:hover`, `.popup-notification-secondary-button:hover`, `.autocomplete-richlistitem:hover`, `menuitem:hover`, `#editBMPanel_*:hover` elements, `#protections-popup-info-button:hover`, `.unified-extensions-item-menu-button:hover` | Applies `--uc-hover-color` to all hoverable buttons and list items in panels and popups. |
| `.unified-extensions-item-menu-button.subviewbutton` | Removes all padding (second rule; overrides any previously set padding). |
| `#urlbar-one-offs-header-label` | Hides the "Search with" header label above the one-off search engine buttons. |
| `#unified-extensions-button` | Adds `10px` right margin to the unified extensions (puzzle-piece) toolbar button. |
| `#tabbrowser-tabpanels` | Sets the background of the area behind all tab panels to `--uc-main-bgcolor`. |
