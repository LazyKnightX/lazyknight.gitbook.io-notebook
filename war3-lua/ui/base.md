# Base | 基类

|     名字      | 说明                    |
| ------------- | ----------------------- |
| [:set_position](#ui_base_set_position) | 设置相对坐标            |
| [:set_alpha](#ui_base_set_alpha) | 设置可见度    |

# :set_position 设置相对坐标

<a name="ui_base_set_position"></a>

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

# :set_alpha 设置可见度

<a name="ui_base_set_alpha"></a>

1=可见  0=不可见

大于1时，采用0~255规则；小于等于1时，采用0~1规则。（这会导致隐患，如果缓慢变化alpha恰好为1，会出现UI闪烁。）

**参数：**

| 名字 | 类型   | 说明                    |
| ---- | ------ | ----------------------- |
| value | number | 可见度，取值：0~1，0~255 |



**用例：**

```lua
control:set_alpha(0)
control:set_alpha(1)
control:set_alpha(255)
```
