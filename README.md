# Zed IDE Cheatsheet (macOS)

This project provides a lightning-fast, native-feeling shortcuts cheatsheet for the Zed IDE on macOS. Instead of context-switching to a web browser or squinting at a PDF, this setup uses a custom Zed Task and macOS's native Quick Look (`qlmanage`) to render a beautiful, single-page overlay instantly over your code that is dismissed when you hit Esc.

The cheatsheet is designed as a lightweight, 3-column HTML file styled with the Catppuccin Mocha color palette to perfectly match modern dark themes. It covers all essential keybindings—from navigation and editing to multi-cursor magic—and fits entirely on a single screen without scrolling.

Because it is built on standard HTML & CSS, it is infinitely customizable. You can easily modify the shortcuts, add project-specific notes, or tweak the styling, all while keeping your hands on the keyboard using a simple trigger.

Here is the setup:

1. The Content (Compact HTML)

Place `zed-cheatsheet.html` on a known path, like `~/.config/zed/`.

2. The "On Demand" Trigger (Zed Task)

We will create a custom Zed Task that triggers macOS's native `qlmanage`. This forces a popup window to appear over Zed.

Open Zed. Press <key>Cmd</key> + <key>Shift</key> + <key>P</key> and type `task: open tasks`.

This opens your `tasks.json`. Add the following entry inside the brackets:

```JSON
[
  {
    "label": "Show Cheatsheet",
    "command": "qlmanage -p ~/.config/zed/cheatsheet.html >/dev/null 2>&1",
    "use_new_terminal": false,
    "hide": "always",
  }
]
```

You need to bind a specific key (like <key>Cmd</key> + <key>?</key>) to trigger this specific task instantly.

Open your Keymap: <key>Cmd</key> + <key>Shift</key> + <key>P</key>, type `Open Keymap`, and press Enter.

Add this entry to your keymap.json:

```JSON
[
  {
    "context": "Workspace",
    "bindings": {
      "cmd-?": ["task::Spawn", { "task_name": "Show Cheatsheet" }]
    }
  }
]
```

> Make sure the task_name matches the "label" in your `tasks.json` exactly.


3. How to use it

Now, you can just press <key>Cmd</key> + <key>?</key> (which is <key>Cmd</key> + <key>Shift</key> + <key>/</key>) and your cheatsheet overlay will appear instantly.

A floating window with the 3-column cheatsheet will appear centered on your screen.

Press <key>Esc</key> to dismiss it instantly.

> The first time you run it, macOS might ask for permission to access the folder/file. Click OK.

This project was inspired by the very useful https://cheatsheets.zip/zed.
