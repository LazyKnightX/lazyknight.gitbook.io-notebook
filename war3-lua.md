# War3 Lua

# API

## 内置UI接口

### 基类

|     名字      | 说明                    |
| ------------- | ----------------------- |
| :set_position | 设置相对坐标            |

#### :set_position 设置相对坐标

支持移动到屏幕外

已解锁普通控件的屏幕限制



**参数：**

| 名字 | 类型   | 说明                    |
| ---- | ------ | ----------------------- |
| x    | number | 相对父控件偏移坐标 x 轴 |
| y    | number | 相对父控件偏移坐标 y 轴 |



**用例：**

```lua
control:set_position(x, y)
```