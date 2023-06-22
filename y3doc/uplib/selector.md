# 筛选器

>筛选器为编辑器内动态创建的一个逻辑结构，作用是筛选出目标范围内的对象（单位、可破坏物等）。


## 事件


## 方法

### 对投射物所在点300范围内的敌方单位造成伤害
```lua
for _,target in up.selector()
    :in_range(effect:get_point(),300)
    :is_enemy(unit)
    :ipairs()
do
    unit:damage{
        target = target,
        skill = skill,
        damage = damage,
    }
end
```