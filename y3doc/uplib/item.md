# 物品

> 在物编中新建或定制物品，并配置关联的模型与技能。

物品是一个虚拟的对象，它有两个形态，地面 和 持有。

## 事件

### 物品选中事件
```lua
--player为选中物品的玩家 item为被选中的物品id
up.game:event('物品-选中',function(_,player,item)

end)
```
## 方法

### 新建物品
```lua
local item = up.create_item(point,id,player)
```

### 设置物品名称
```lua
item:set_name(name)
```

