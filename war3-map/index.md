# 魔兽地图开发笔记

骑老登的魔兽地图开发笔记。

* [内置Lua / 内置JAPI](https://war3rpg.top)

## Button - Sync Click

```lua
button = {
    type = 'button',
    sync_key = 'UNIQUE-SYMBOL',
    on_sync_button_clicked = function(self, player)
        ... stuffs here
    end,
}
```
