# Emit `node_remove` when replacing receptacles

Fixes [bspwm issue #1531](https://github.com/baskerville/bspwm/issues/1531).

When a window replaces a receptacle, the receptacle was freed without
emitting `node_remove`. This patch emits the missing event.

Upstream pull request:
[PR #1553](https://github.com/baskerville/bspwm/pull/1553)

Base commit: `e11eff4`.

Apply with:

```sh
git apply 0001-emit-node-remove-for-receptacle.patch
```
