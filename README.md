# wl-logoped
A logopedist for Wayland since it seems almost impossible to output non-ASCII characters, atleast in Chromium-based applikations.

# Dependencies
- [`wl-clipboard`](https://github.com/bugaevc/wl-clipboard)
- [`wtype`](https://github.com/atx/wtype)

# Usage

```sh
wl-logoped <string> [timeout] [paste keystroke]
```
```sh
# Default values:
  timeout         : 0.05
  paste keystroke : -M ctrl -k v -m ctrl
```
> Since we save the string in `wl-clipboard`, a timeout is used to give time for the paste to complete before restoring the clipboard we temporarily overwrote.  
> **If your output is not the string you inputted, try increasing the timeout.**
 
> Almost everything use the default ctrl+v, but it can be changed if you need to.  
> The keystroke syntax is the same as for [`wtype`](https://github.com/atx/wtype)

#### Example: Output éûÄ¤ with ctrl+shift+v as paste and default timeout
```sh
wl-logoped 'éûÄ¤' '' '-M ctrl -M shift -k v -m ctrl -m shift'
```
> Note that we must leave `[timeout]` as an empty string

#### Example: Output 🥔 with a 1 second timeout and default keystroke for paste
```sh
wl-logoped '🥔' '1.0'
```

# How to actually use it 
Use something like [xremap](https://github.com/xremap/xremap) to assign a key.
I use this on my Nordic ISO keyboard with `us` as the layout:
> `KEY_102ND` is not normally used since `us` layout is ANSI which doesn't have that key
```yml
virtual_modifiers:
  - KEY_102ND

shared:
  needs_logopedist: &needs_logopedist
    - brave-browser
    - chromium

keymap:
  - application:
      only: *needs_logopedist
    remap:
      KEY_102ND-KEY_SEMICOLON: { launch: ["wl-logoped", "ö"] }
      KEY_102ND-SHIFT-KEY_SEMICOLON: { launch: ["wl-logoped", "Ö"] }

  # For applications that support it, it's better to use wtype
  - application:
      not: *needs_logopedist
    remap:
      KEY_102ND-KEY_SEMICOLON: { launch: ["wtype", "ö"] }
      KEY_102ND-SHIFT-KEY_SEMICOLON: { launch: ["wtype", "Ö"] }
```


# Problems with alternative methods

| Tool       | Issue                                                    |
|------------|----------------------------------------------------------|
| `wtype`    | Doesn't work in Chromium (at least)                      |
| `ydotool`  | Doesn't work if keyboard layout is missing the character |
| `wlrctl`   | Only ASCII strings are currently supported               |
| `dotool`   | `dotool: WARNING: impossible character for layout: ä`    |

# Related Issues

- https://github.com/atx/wtype/issues/31
- https://github.com/ReimuNotMoe/ydotool/issues/22


# Squirrel, cause why not

<img width="1032" height="774" alt="image" src="https://github.com/user-attachments/assets/217f389b-4496-425e-a726-468e35d8fae6" />
https://www.deviantart.com/easterngraysquirrel/art/Squirrel-152-Peanut-521104833
