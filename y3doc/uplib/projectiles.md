# 投射物

> 投射物一般用于制作拥有一定逻辑的非单位对象，如一有人进入10m内就会爆炸的地雷，远程攻击的弹道等。

## 事件


## 方法

### 新建投射物在单位挂接点
```lua
local Particle = unit.add_effect(self,data)

-- data包含以下参数
--  id      投射物id
--  socket  挂接点
--  angle   角度
--  target  目标单位
--  skill   关联技能
```

### 移除投射物
```lua
projectiles:remove()
```

