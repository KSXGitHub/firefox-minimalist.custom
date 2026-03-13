# userChrome.css

This is the main entry-point stylesheet for the Firefox UI customization. Firefox loads this file from the `chrome` profile folder when `toolkit.legacyUserProfileCustomizations.stylesheets` is set to `true`.

It imports all the component stylesheets from the `content/` directory in the following order:

| Import | Purpose |
|--------|---------|
| `content/navbar_tabs_responsive_oneliner.css` | Merges the navigation bar and tab strip into a single row |
| `content/autohide_bookmarks_toolbar.css` | Hides the bookmarks toolbar and reveals it on hover |
| `content/compact_proton.css` | Reduces spacing throughout the UI to match the old compact density |
| `content/minimal_text_fields.css` | Makes the URL bar and search fields transparent and minimal |
| `content/compact_extensions_panel.css` | Condenses the unified extensions panel |
| `content/theme.css` | Applies the dark color palette and all theme-specific overrides |

See the markdown file alongside each imported CSS file for a detailed description of the rules it contains.
