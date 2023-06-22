# 魔法效果

> 魔法效果是一种对单位的持续影响，一般会被用来制作dot伤害或者异常状态（需要注意它与单位状态的区别）。

## 事件

### 失去魔法效果事件
```lua
--unit为失去魔法效果的单位 buff为失去的魔法效果
up.game:event('魔法效果-失去',function(_,unit,buff)

end)
```
## 方法

### 给单位添加魔法效果
```lua
unit:add_buff(buff_id,data)
-- data 是数据表，包含以下参数
--   source     来源单位
--   skill      来源技能
--   time       持续时间
--   updata     循环周期
--   stack      层数

-- 示例
local buff = unit:add_buff(buff_id,{
    source = source_unit,
    skill = source_skill,
    time = 5
})
```

### 遍历单位身上的魔法效果
```lua
for buff in unit:each_buff() do
    buff:remove()
end
```

### 移除单位身上某种类型的魔法效果
```lua
unit:remove_buff(buff_id)
```

### 移除魔法效果
```lua
buff:remove()
```


### 构建魔法效果示例
```lua
--声明魔法效果类型 134225487是物体编辑器中魔法效果ID
local mt = up.buff[134225487]

--获得魔法效果时触发
function mt:on_add()

end

--失去魔法效果时触发
function mt:on_remove()

end

--循环周期触发
function mt:on_pulse()
    --魔法效果来源
    local unit = self.source
    up.particle{
        model = 100711,
        target = unit:get_point(),
        speed = 2,
        time = 1,
    }
    --对周围敌人造成伤害
    local damage = unit:get'物理攻击'
    for _,target in up.selector()
        :in_range(unit:get_point(),400)
        :is_enemy(unit)
        :ipairs()
    do
        up.particle{
            model = 101873,
            target = target,
            socket = 'hit_point',
            time = 1,
        }
        unit:damage{
            target = target,
            damage = damage,
            type = '物理',
        }
    end
end

```