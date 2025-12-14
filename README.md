Since Zed's terminal is small, the best approach is to use a macOS Native "Quick Look" window. This creates a floating, dark-mode overlay that pops up over Zed when you need it and vanishes when you hit Esc.

Here is the setup:

1. The Content (Compact HTML)

We will use HTML instead of Markdown because it allows us to split the content into 3 columns so it fits on one screen.

To achieve a single-page view without scrolling, we need to move away from a vertical list (Markdown) and use a Multi-Column Grid.

Since Zed's terminal is small, the best approach is to use a macOS Native "Quick Look" window. This creates a floating, dark-mode overlay that pops up over Zed when you need it and vanishes when you hit Esc.

Here is the setup:

1. The Content (Compact HTML)

We will use HTML instead of Markdown because it allows us to split the content into 3 columns so it fits on one screen.

Place `zed-cheatsheet.html` inside `~/.config/zed/`:

2. The "On Demand" Trigger (Zed Task)

We will create a custom Zed Task that triggers macOS's native `qlmanage`. This forces a popup window to appear over Zed.

Open Zed.

Press <key>Cmd</key> + <key>Shift</key> + <key>P</key> and type `task: open tasks`.

This opens your `tasks.json`. Add the following entry inside the brackets:

```JSON
[
  {
    "label": "Show Cheatsheet",
    "command": "qlmanage -p ~/.config/zed/cheatsheet.html >/dev/null 2>&1",
    "use_new_terminal": false,
    "hide": "always",
    "keep_alive": false
  }
]
```

3. How to use it

Now, whenever you need the cheatsheet:

Press <key>Cmd</key> + <key>Shift</key> + <key>P</key>.

Type `Show Cheatsheet` (or just `Show`) and hit Enter.

A floating window with the 3-column cheatsheet will appear centered on your screen.

Press <key>Esc</key> to dismiss it instantly.

(Note: The first time you run it, macOS might ask for permission to access the folder/file. Click OK.)
