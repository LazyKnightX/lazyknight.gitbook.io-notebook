# 异步计时器

## game.loop

game.wait | game.loop | game.timer

以上三者会在本地状态下运行，应当仅用于实现异步渲染逻辑。

Sample 1

```lua
game.loop(10, function()
    local plr = get_local_player()
    if plr:is_self() then
        -- 本地渲染动作
    end
end)
```
