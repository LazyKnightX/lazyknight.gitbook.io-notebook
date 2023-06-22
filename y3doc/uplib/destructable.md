# 可破坏物

> 可破坏物是一种特殊的装饰对象，可以被破坏并且改变形态，同时也可以作为采集技能的目标。

## 事件

### 可破坏物选中事件
```lua
up.game:event('可破坏物-选中',function(_,player,destructible)--player为选中可破坏物的玩家 destructible为被选中的可破坏物id

end)
```
## 方法

### 新建可破坏物
```lua
local destructable = up.create_destructable(id, point, angle, scale)
```

### 设置可破坏物名称
```lua
destructable:set_name(name)
```

### 删除可破坏物
```lua
destructable:remove()
```

