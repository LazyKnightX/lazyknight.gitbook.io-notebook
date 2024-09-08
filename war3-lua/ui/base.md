# 魔兽Lua/UI/基类

## Base | 基类

| 名字                                      | 说明     |
| --------------------------------------- | ------ |
| [:set\_position](base.md#set\_position) | 设置相对坐标 |
| [:set\_alpha](base.md#set\_alpha)       | 设置可见度  |

## :set\_position <a href="#set_position" id="set_position"></a>

设置相对坐标

支持移动到屏幕外

已解锁普通控件的屏幕限制

**参数：**

| 名字 | 类型     | 说明            |
| -- | ------ | ------------- |
| x  | number | 相对父控件偏移坐标 x 轴 |
| y  | number | 相对父控件偏移坐标 y 轴 |

**用例：**

```lua
control:set_position(x, y)
```

## :set\_alpha <a href="#set_alpha" id="set_alpha"></a>

设置可见度

1=可见 0=不可见

大于1时，采用0-255规则；小于等于1时，采用0-1规则。（这会导致隐患，如果缓慢变化alpha恰好为1，会出现UI闪烁。）

**参数：**

| 名字    | 类型     | 说明                 |
| ----- | ------ | ------------------ |
| value | number | 可见度，取值：0~~1，0~~255 |

**用例：**

```lua
control:set_alpha(0)
control:set_alpha(1)
control:set_alpha(255)
```
