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
- `pastering [1,2,3...]` - Restores item `N` to your active clipboard. (e.g., `pastering 1` copies the previous copied item back into your current clipboard).
- `pastering show [N]` - Prints out the full text of the `N`th item in your clipboard history (0 = current, 1 = previous, etc).
- `pastering show` - Display all saved clips.
- `pastering stop` - Stops the daemon.


