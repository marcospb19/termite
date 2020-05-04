# Termite fork

This is a fork of [termite](https://github.com/thestinger/termite).

# Why a fork?

With this fork, the configuration file supports the keyword `include`.

```ini
include file1
include file2
```

This means that the configuration can be divided in other files, and the include keyword will \
put it all together on a final file named `config` in the same directory.

# Example of config setup

Call command: `termite --custom-config ~/.config/termite/custom`

Files inside of `~/.config/termite/`
```zsh
custom
colors
```

Content of `custom` file:

```ini
[options]
bold_is_bright = true
font = Monospace 10
include colors
...
```

Content of `colors` file:
```ini
[colors]
# If unset, will reverse foreground and background
highlight = #2f2f2f

# Colors from color0 to color254 can be set
color0 = #3f3f3f
color1 = #705050
...
```

`config` file will be created at the same directory with the following content:

```ini
[options]
bold_is_bright = true
font = Monospace 10

[options]
bold_is_bright = true
font = Monospace 10

# # Included from: /home/user/.config/termite/colors
[colors]
# If unset, will reverse foreground and background
highlight = #2f2f2f

# Colors from color0 to color254 can be set
color0 = #3f3f3f
color1 = #705050
...
# #
...
```

# Observations
Note that `custom` and `colors` are just example names, it can be any other. \
**Don't use the file named `config`, because it will be overwritten.**
