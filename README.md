# wl-logoped
A logopedist for Wayland since it seems almost impossible to output non-ASCII characters, atleast in Chromium-based applikations.

# Usage

```sh
wl-logoped <String>
```
Use something like [xremap](https://github.com/xremap/xremap) to assign a key.
I use this on my Nordic ISO keyboard using a `us` as layout:
```yml
virtual_modifiers:
  - KEY_102ND

keymap:
 -  name: Some european letters
    remap:
      KEY_102ND-LEFTBRACE: { launch: ["wl-logoped", "å"] }
      KEY_102ND-SHIFT-KEY_LEFTBRACE: { launch: ["wl-logoped", "Å"] }

      KEY_102ND-KEY_APOSTROPHE: { launch: ["wl-logoped", "ä"] }
      KEY_102ND-SHIFT-KEY_APOSTROPHE: { wl-logoped: ["wtype", "Ä"] }

      KEY_102ND-KEY_SEMICOLON: { launch: ["wl-logoped", "ö"] }
      KEY_102ND-SHIFT-KEY_SEMICOLON: { launch: ["wl-logoped", "Ö"] }

      KEY_102ND-KEY_E: { launch: ["wl-logoped", "é"] }
      KEY_102ND-SHIFT-KEY_E: { launch: ["wl-logoped", "É"] }

      KEY_102ND-KEY_U: { launch: ["wl-logoped", "ü"] }
      KEY_102ND-SHIFT-KEY_U: { launch: ["wl-logoped", "Ü"] }
```
> `KEY_102ND` is not normally used since `us` layout is ANSI which doesn't have that key

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
