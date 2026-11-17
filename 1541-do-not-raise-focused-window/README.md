# bspwm patches

Local patches for [bspwm](https://github.com/baskerville/bspwm).

## `0001-do-not-raise-focused-window.patch`

Fixes an unwanted raise of the focused floating window when switching
desktops with `focus_follows_pointer=true`.

Related upstream work:

- [Issue #1537](https://github.com/baskerville/bspwm/issues/1537)
- [Issue #1540](https://github.com/baskerville/bspwm/issues/1540)
- [PR #1541](https://github.com/baskerville/bspwm/pull/1541)

The bug was reproduced with bspwm 0.9.12 on Slackware Linux. This patch is
based on commit `c5cf7d3` and also preserves the previous `auto_raise` value.

Apply to a clean bspwm 0.9.12 checkout:

```sh
git apply 0001-do-not-raise-focused-window.patch
make
```
