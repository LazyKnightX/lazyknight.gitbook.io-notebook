# 玩家

>地图的玩家数量在[玩家设置]中定义。玩家可以是 **用户** 或 **电脑** 。


## 事件

### 玩家发送消息事件
```lua
--player为发送消息的玩家 player为消息内容
up.game:event('玩家-发送消息',function(_,player,msg)

end)
```
## 方法

### 获取玩家
```lua
local player = up.player(1)
```

### 获取玩家名称
```lua
local name = player:get_name()
```
