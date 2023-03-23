# War3 RPG \[CH]

# war3rpg.top framework

## 技能冷却渲染机制

原生冷却时间遮罩的100%对应的是技能的基础冷却时间。
当基础冷却时间为10秒时，如果设置当前剩余冷却时间为20，则前10秒会始终保持100%进度，后10秒才会开始可见。

当CD遮罩动画正在“过程中”时，修改基础冷却时间不会影响本次播放。
当播放结束后（或开始前），修改基础冷却时间为20秒，可以修正前述的前10秒进度问题。

（注：修改基础冷却时间之类涉及物编的数据时，需要重新触发一次单位GUI刷新才可以看到效果。）

修改指定单位持有技能的基础冷却时间：

```lua
local gid = s2gid(gid_s)
local lv = 1 --影响的物编技能等级
local time = 5 --单位：秒
local data_id = 105 --物编：魔法施放时间间隔 - Cool1 Cool2 Cool3 .. Cool{lv}
YDWESetUnitAbilityDataReal(j_unit, gid, lv, data_id, time)
```

修改指定单位持有技能的当前剩余冷却时间：

```lua
local gid = s2gid(gid_s)
japi.EXSetAbilityState(japi.EXGetUnitAbility(j_unit, gid), 1, time_remains)
```

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
