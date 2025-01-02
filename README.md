# XMenu

## A suckless-style run launcher

### Requirements

- `gcc` (or any other C99 compiler)
- `make`
- `pkg-config`
- `libX11`
- `libXft`

### Building

- `cd src`
- Modify `config.mk` to fit your enviroment (you probably want to change `INSTALL_DIR` from `~/.opt` to `/usr/local/bin` or `/usr/bin`
- `make` (to generate a binary in the current directory)
or:
- `make install` (to install to `INSTALL_DIR`)

> **NOTE:** `make install` will install `xmenu`, as well as `xmenu_run` to the system.

### Usage

XMenu works similar to other run-launchers like fzf and dmenu.\
It takes newline delimited strings from `stdin` as input, gives you a prompt, then writes the selected entry back to `stdout`.

> **NOTE:** XMenu will always remove duplicate strings from its given input

**Examples:**

- `echo "foo\nbar\nbaz" | xmenu`
- `xmenu < somefile.txt`
```sh
xmenu
foo
bar
baz
^D
```

This gives it a lot of potential for usage in shell scripts.\
A script for using XMenu as a launcher for desktop applications can be found at `src/xmenu_run`.

## Configuration

Configuration is done by editing `src/config.h`, and rebuilding the source code.

## Keybindings

The keybindings are generally inspired by GNU readline and Vim, aiming to satisfy both kinds of users.

- Move cursor up: `<C-p>`, `<C-k>`, `<Up>`
- Move cursor down: `<C-n>`, `<C-j>`, `<Down>`
- Clear selection: `<C-u>`
- Quit: `<ESC>`, `<C-c>`
- Select entry: `<CR>`

## Command Line Options

- `-e`: enumerate output (useful for scripting)
  - Enumeration will start at 1
  - if the selected query does not exist within the given list of strings, the returned value will be 0
- `-h`: print usage
- `-v`: print version
