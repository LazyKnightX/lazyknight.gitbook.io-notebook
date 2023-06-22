# 特效

> 特效是一种纯表现对象，可以直接放在场景中或者由触发器创建。

## 事件



## 方法

### 在单位挂接点新建特效
```lua
local particle = unit.up.particle(self,data)
-- data包含以下参数
--    target            单位或点
--    model             模型
--    id                特效id
--    socket            挂接点
--    angle             角度
--    target            目标单位
--    skill             关联技能
--    follow_rotation   跟随单位旋转
--    follow_scale      跟随单位缩放
--    time              持续时间
--    scale             缩放
--    speed             播放速度
```

### 移除特效
```lua
particle:remove()
```

