# wl-logoped
A logopedist for Wayland since it seems almost impossible to output non-ASCII characters, atleast in Chromium-based applikations.

# Usage

```sh
wl-logoped <String> [-]
```
The optional `-` flag makes the command use your regular clipboard instead of the primary selection.  
This will overwrite whatever you currently have copied to your regular `wl-clipboard`.

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

- wtype - don't work in chromium Chromium (atleast)
- ydotool - don't work if keyboard layout is missing the char
- wlrctl - Only ascii strings are currently supported
- dotool - `dotool: WARNING: impossible character for layout: ä`

# Related Issues

- https://github.com/atx/wtype/issues/31
- https://github.com/ReimuNotMoe/ydotool/issues/22


# Squirrel, cause why not

<img width="1032" height="774" alt="image" src="https://github.com/user-attachments/assets/217f389b-4496-425e-a726-468e35d8fae6" />
https://www.deviantart.com/easterngraysquirrel/art/Squirrel-152-Peanut-521104833
