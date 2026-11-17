# Fix stale presel feedback with `single_monocle`

Fixes [bspwm issue #1548](https://github.com/baskerville/bspwm/issues/1548).

With `single_monocle=true`, presel feedback could remain visible after
switching desktops. The fix makes `hide_node()` and `show_node()` use
`user_layout`, matching `draw_presel_feedback()`.

Upstream pull request:
[PR #1552](https://github.com/baskerville/bspwm/pull/1552)

Base commit: `e11eff4`.

Apply with:

```sh
git apply 0001-fix-presel-feedback-single-monocle.patch
```
