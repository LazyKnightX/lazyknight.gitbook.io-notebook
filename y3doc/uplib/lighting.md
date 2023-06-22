# 链接特效

> 链接特效是一种特效类型，一般用来做链条链接效果，起点和终点可以是单位也可以是地点。

## 事件


## 方法

### 新建链接特效
```lua

local lightning = up.lightning(data) 
-- data包含以下参数
--    id                链接特效id
--    life              持续时间
--    source            起点/起始单位
--    source_height     起点偏移高度
--    source_socket     起点单位挂接点
--    target            终点/终点单位
--    target_height     终点偏移高度
--    target_socket     终点单位挂接点
```

### 移除链接特效
```lua
lightning:remove()
```

