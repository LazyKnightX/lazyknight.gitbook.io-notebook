# 界面

## 事件

### 触发任意ui事件后输出触发玩家和事件名
```lua
up.game:event('UI-事件', function(self, player,event)
    print(player)
    print(event)
end)
```
## 方法
### 通过路径获取ui
```lua
local ui = up.get_ui(path, _player)
```
### 设置控件位置
```lua
up.ui:set_position(ui,{x,y},player)
```

### 设置控件大小
```lua
up.ui:set_size(ui,{w,h},player)
```

### 设置控件缩放
```lua
up.ui:set_scale(ui,{w,h},player)
```

### 设置控件层级
```lua
up.ui:set_z_order(ui,z_order,player)
```

### 设置控件图片
```lua
up.ui:set_image(ui,image_id,player)
```