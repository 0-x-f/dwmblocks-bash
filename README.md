# 🧱 dwmblocks

This project is fork of [dwmblocks](https://github.com/torrinfail/dwmblocks).

Features:
- Signals
- Separator

## 📦 Install

```
git clone https://github.com/0-x-f/dwmblocks-bash
cd dwmblocks-bash
chmod +x dwmblocks
./dwmblocks &
```

## 🚀 Autostart

```
mkdir -p ~/.local/bin
mv dwmblocks ~/.local/bin
```

Edit $PATH in the script that launch dwm:

```sh
...

export PATH="$PATH:$HOME/.local/bin"

dwmblocks &

...
```

## ⚡️ Signals

For update one of the blocks, send the signal `kill -SID PID`. That signal can be bind a hotkey in dwm.
Example for updating keyboard layout on press Alt+Shift:

Getting PID:

```
pgrep -a dwmblocks | awk '{ printf $1 }'
```

Edit `config.h`:

```c
/* Update keyboard layout */
static const char update_layout[] = "kill -36 $(pgrep -a dwmblocks | awk '{ printf $1 }')";

...

static const Key keys[] = {
	...
	{ 0, XK_Alt_L|XK_Shift_L, spawn, SHCMD(update_layout) },
	...
}
```

Compile and reboot dwm. Now bind is working fine.


