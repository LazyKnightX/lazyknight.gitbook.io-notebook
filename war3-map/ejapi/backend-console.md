# 黑窗控制台

使用内置Lua打开黑窗控制台以后，如果使用左键选中了控制台内容，此时游戏会被阻断。

因此如果在运行游戏的同时会显示控制台的情况下，如果你发现游戏卡住了，先尝试用鼠标在控制台按下右键，以清空当前的选择。

## 开启黑窗控制台

```lua
local console = require 'jass.console'
console.enable = true
```

## 关闭黑窗控制台

```lua
local console = require 'jass.console'
console.enable = false
```
