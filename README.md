# wl-logoped
A logopedist for Wayland since it seems almost impossible to output non-ASCII characters, atleast in Chromium-based applikations.

# Usage

```sh
wl-logoped <String>
```
Use something like [xremap](https://github.com/xremap/xremap) to assign a key.
I use this on my Nordic ISO keyboard with `us` as the layout:
> `KEY_102ND` is not normally used since `us` layout is ANSI which doesn't have that key
```yml
# wl-logoped.yml

virtual_modifiers:
  - KEY_102ND

keymap:
 -  name: Some european letters for stuff that hate wtype
    only: [brave-browser, vesktop]
    remap:
      KEY_102ND-LEFTBRACE: { launch: ["wl-logoped", "å"] }
      KEY_102ND-SHIFT-KEY_LEFTBRACE: { launch: ["wl-logoped", "Å"] }

      KEY_102ND-KEY_APOSTROPHE: { launch: ["wl-logoped", "ä"] }
      KEY_102ND-SHIFT-KEY_APOSTROPHE: { launch: ["wl-logoped", "Ä"] }

      KEY_102ND-KEY_SEMICOLON: { launch: ["wl-logoped", "ö"] }
      KEY_102ND-SHIFT-KEY_SEMICOLON: { launch: ["wl-logoped", "Ö"] }

      KEY_102ND-KEY_E: { launch: ["wl-logoped", "é"] }
      KEY_102ND-SHIFT-KEY_E: { launch: ["wl-logoped", "É"] }

      KEY_102ND-KEY_U: { launch: ["wl-logoped", "ü"] }
      KEY_102ND-SHIFT-KEY_U: { launch: ["wl-logoped", "Ü"] }
```
For applications that support it, it's better to use `wtype`:
```yml
# wtype.yml

virtual_modifiers:
  - KEY_102ND

keymap:
 -  name: Some european letters for stuff that respects wtype
    remap:
      KEY_102ND-LEFTBRACE: { launch: ["wtype", "å"] }
      KEY_102ND-SHIFT-KEY_LEFTBRACE: { launch: ["wtype", "Å"] }

      KEY_102ND-KEY_APOSTROPHE: { launch: ["wtype", "ä"] }
      KEY_102ND-SHIFT-KEY_APOSTROPHE: { launch: ["wtype", "Ä"] }

      KEY_102ND-KEY_SEMICOLON: { launch: ["wtype", "ö"] }
      KEY_102ND-SHIFT-KEY_SEMICOLON: { launch: ["wtype", "Ö"] }

      KEY_102ND-KEY_E: { launch: ["wtype", "é"] }
      KEY_102ND-SHIFT-KEY_E: { launch: ["wtype", "É"] }

      KEY_102ND-KEY_U: { launch: ["wtype", "ü"] }
      KEY_102ND-SHIFT-KEY_U: { launch: ["wtype", "Ü"] }
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
