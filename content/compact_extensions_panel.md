# compact_extensions_panel.css

**Source:** [MrOtherGuy/firefox-csshacks](https://github.com/MrOtherGuy/firefox-csshacks/tree/master/chrome/compact_extensions_panel.css) — Mozilla Public License v. 2.0

Condenses the unified extensions panel by reducing padding, hiding the message-deck description text, and shrinking extension icons. Useful when many extensions are installed.

## CSS Variables

| Variable | Declared on | Purpose |
|----------|-------------|---------|
| `--uei-icon-size` | `#unified-extensions-view` | Sets the size of extension icons inside the panel to `16px`. |

## CSS Rules

| Selector | Purpose |
|----------|---------|
| `#unified-extensions-view` | Declares `--uei-icon-size: 16px` to reduce extension icon size inside the panel. |
| `.unified-extensions-item-menu-button.subviewbutton` | Removes all padding and the inline-end margin from the per-extension menu (⋮) button so it takes up minimal space. |
| `.unified-extensions-item-action-button.subviewbutton` | Reduces the block (top/bottom) padding of the main extension action button to `6px`. |
| `.unified-extensions-item-menu-button.subviewbutton > .toolbarbutton-icon` | Adds `4px` of padding around the icon inside the menu button for a comfortable click target. |
| `.unified-extensions-item-message-deck` | Hides the message-deck area (the secondary description shown below an extension's name) to save vertical space. |
| `#unified-extensions-view > vbox > vbox > .unified-extensions-item` | Removes all block padding from each extension row in the main panel list. |
| `#unified-extensions-panel .unified-extensions-item` | Removes the block margin between extension rows in the panel. |
