# Firefox-Minimalist

![](https://i.imgur.com/nFTXrH9.png)
This is a clean and minimal theme for the Firefox Browser <br>
Created and Functional on Windows 11 with version 136.0 of [Firefox](https://www.mozilla.org/en-US/firefox/releases/). <br>

This theme uses stylesheets from the [MrOtherGuy firefox-csshacks](https://github.com/MrOtherGuy/firefox-csshacks) repository.

# Download

You can download the files by clicking [**HERE**](https://github.com/eduwz/firefox-minimalist/archive/refs/heads/master.zip).

# Installation

In the Firefox **Address Bar**, navigate to `about:config` and accept the risks<br>
Search for `toolkit.legacyUserProfileCustomizations.stylesheets` and toggle it to `true` (by double clicking on it)
    
In the Firefox **Address Bar**, navigate to `about:support`, Search for **Profile Folder** and click on the **Open Folder** button <br>
Create a new folder and name it `chrome` (with lowercase) <br>

Unzip and paste the downloaded files inside the **chrome folder** <br>
Restart Firefox, and enjoy your new theme!

# File overview

| File | What it styles |
|------|---------------|
| `userChrome.css` | **Browser chrome** — everything that surrounds the web page: toolbars, tabs, menus, sidebar, pop-ups, and any panel that is part of the Firefox UI itself. Changes here are invisible to web pages. |
| `userContent.css` | **Page content** — styles that are injected *into* web pages loaded by Firefox. This theme uses it to restyle Firefox's own built-in pages (`about:newtab`, `about:home`, `about:blank`, etc.) so their colours match the dark theme. It has no effect on normal websites unless you explicitly target them. |

In short: `userChrome.css` = the browser window frame; `userContent.css` = what is inside the frame.
