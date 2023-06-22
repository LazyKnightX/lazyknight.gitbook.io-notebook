# 计时器

> 计时器的精度为1毫秒，每当计时器到期便会执行回调函数。

## 事件


## 方法

### 创建计时器
```lua
-- 每1秒执行一次，执行10次
local timer = up.timer(1, 10, function (timer)
end)
```

### 创建循环计时器
```lua
-- 每1秒执行一次，直到手动移除触发器
local timer = up.loop(1, function (timer)
end)
```

### 创建单次计时器
```lua
-- 在1秒后执行一次
local timer = up.wait(1, function (timer)
end)
```

## 暂停
```lua
timer:pause()
```

### 移除
```lua
timer:remove()
```
