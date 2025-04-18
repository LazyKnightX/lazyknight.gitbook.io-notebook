# UI异步行为转同步

使用内置Lua进行制图时常常需要处理各类本地UI操作，这些操作发生在某个玩家的本机上。

此时为了让这个操作能够被所有玩家都接收到，需要进行消息转发操作。



### 准备工作

`package\plugin\script\ui\server\trigger.lua`

检查上述文件中的同步逻辑是否为**使用网易同步**，如果没有，则修改为使用网易同步，否则会无效。



### 写法

```lua
-- 开头代码：必要的工具引入
local client = require 'ui.client.util'

-- 中间代码：各类UI组件和逻辑
-- （这里略）

-- 结尾代码：注册点击回调事件
local server = require 'ui.server.util'

local event = {
    ['action_select_card_button'] = function(被点击的卡片ID)
        local 玩家句柄 = server.player.handle
        local 玩家ID = GetConvertedPlayerId(玩家句柄)

        print('同步-点击按钮', 被点击的卡片ID, '玩家ID', 玩家ID)
    end,
}

server.register_event('gui_74_3in1', event)

-- 调用处代码：
client.send_message({
    type = 'gui_74_3in1',
    func_name = 'action_select_card_button',
    params = { 被点击的卡片ID }
}, false)
```
