# macOS per-tab profiles

Adds **Window → Profiles** to Ghostty. Selecting a profile updates every existing
split in the selected tab. Other tabs and windows stay unchanged.

Create `~/.config/ghostty/profiles/` and add a file such as `red.ghostty`:

```ini
theme = Catppuccin Mocha
background = #240b0b
```

Select a tab, then choose **Window → Profiles → red**. The menu lists `.ghostty`
files alphabetically and refreshes each time it opens. No restart is needed.

Profiles apply all settings supported by per-surface reload, including fonts,
keybindings, and clipboard behavior. Omitted settings use Ghostty defaults.
Running shells keep their command, environment, and working directory.

To share settings, put them in `~/.config/ghostty/common.ghostty`. Include it
from `~/.config/ghostty/config`:

```ini
config-file = common.ghostty
```

And from each profile:

```ini
config-file = ../common.ghostty
```

Included files load last and override duplicate settings. Keep profile-specific
colors out of the common file.

Invalid or unreadable profiles leave the tab unchanged. Profile selections are
not saved across restarts; new tabs and splits use Ghostty's usual inheritance.
