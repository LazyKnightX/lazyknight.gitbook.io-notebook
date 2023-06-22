# 单位
单位是工程内的主要操作对象，

## 事件
### 单位被创建事件
```lua
up.game:event('单位-创建',function(_,unit)

end)
```
## 方法

### 增加属性
```lua
-- 攻击增加50点
unit:add('攻击', 50)
```

### 添加动画
```lua
unit:add_animation '跳舞'
{
    speed = 1.0,
    loop = false,
}
```

### 增加经验
```lua
unit:add_exp(100)
```
