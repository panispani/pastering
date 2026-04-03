# Paste ring - the simplest macOS clipboard ring buffer

Preserves the last `N` things you copied to your clipboard.

## Dependencies

- **swiftc**: You should have this (type into a terminal to check). If you don't then install with (it's not full xcode, just the command-line tools): `xcode-select --install`

## Installation & Usage

1. Clone this repository.
2. In your terminal, run `./pastering` from this directory, or for convenience (recommended), create symbolic link so you can run it wherever you are:
   `sudo ln -s $(pwd)/pastering /usr/local/bin/pastering`

### Commands

- `pastering start [N]` - Starts the daemon. `N` sets the maximum number of items to keep (defaults to 5 if not specified). This will start a background service that will persists reboots.
- `pastering show [N]` - Prints out the full text of the `N`th item in your clipboard history (1 = current, 2 = previous, etc).
- `pastering [1,2,3...]` - Restores item `N` to your active clipboard. (e.g., `pastering 2` copies the previous copied item back into your current clipboard).
- `pastering show` - Display all saved clips.
- `pastering stop` - Stops the daemon.


## Setting up Global Keyboard Shortcuts on macOS

If you use `pastering 2` frequently (I do!), you can assign them to a global keyboard shortcut via macOS Shortcuts (note that this won't print, it will just copy to your clipboard the previous thing):

1. Open the **Shortcuts.app** (pre-installed on macOS).
2. Click the `+` button in the top right.
3. In the right-hand search bar, search for **"Run Shell Script"** and drag it into the left side (main canvas).
4. Replace the default script with the full path to the `pastering` command, for example:
   ```bash
   /path/to/cloned/repo/pastering show 2
   ```
   or most likely:
   ```
   ~/pastering/pastering show 2
   ```
5. Click the "Info" icon in the top right corner of the window (right side of window).
6. Click **Add Keyboard Shortcut** and press the key combination you want.
7. Click on the top-left next to the minimize-maximize buttons and name the shortcut (e.g., "Paste Ring 2").
8. Close the shortcut window
9. Profit


## (very) Future TODO
- Paste directly. This will likely be a hacky way to "pause" the daemon, copy to clipboard, paste, copy the old thing back, refresh the paste counter and restart the daemon
- Add circular indexing so we don't need to rename files all the time

