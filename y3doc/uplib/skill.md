# 技能

> 技能需要被放置到单位身上由单位使用。

## 事件

### 技能-获得
```lua
function skill:on_add()
   
end
```

### 技能-前摇开始
```lua
function skill:on_cast_start()
   
end
```

### 技能-失去
```lua
function skill:on_remove()
   
end
```

### 使用示例
```lua
--声明技能类型
local mt = up.skill[134256632]

--技能-施法引导时
function mt:on_cast_channel()
    --获取技能拥有者
    local unit = self:get_owner()
    --获取技能目标点/目标单位
    local target = self:get_target()
    local skill = self
    local damage = 100

    if target.type == 'unit' then
        target = target:get_point()
    end

    --对目标点附近敌人造成伤害
    for _,u in up.selector()
        :in_range(target,300)
        :is_enemy(unit)
        :ipairs()
    do
        unit:damage{
            target = u,
            skill = skill,
            damage = damage,
        }
    end
end
```
## 方法

### 添加技能
```lua
--ability_type 隐藏，普攻，通用，英雄
unit:add_skill(ability_type,id,slot)
```

### 增加剩余冷却
```lua
skill:add_cd(1)
```
### 禁用
```lua
skill:disable()
```
### 启用
```lua
skill:enable()
```

### 获取冷却
```lua
local cd = skill:get_cd()
```

### 获取等级
```lua
local level = skill:get_level()
```
