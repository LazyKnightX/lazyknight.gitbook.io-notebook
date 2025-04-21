# UI界面显示与隐藏，菜单按钮的实现

假设存在 `panel` 对象，我们可以通过以下方式来控制它的显示与隐藏。

```lua
local panel = class.panel:builder
{
    type = 'panel',
    x = 0,
    y = 0,
    w = 1920,
    h = 1080,
}

panel:hide() --通过脚本创建的UI，默认是显示的，因此需要在此调用 :hide() 使其隐藏。
```

现在假设存在两个按钮用于控制其显示和隐藏。

```lua
local btnA = class.button:builder
{
    type = 'button',
    x = 100,
    y = 100,
    w = 60,
    h = 20,
    
    m_text = {
        type = 'text',
        x = 0,
        y = 0,
        w = 60,
        h = 20,
        text = '显示'
    },
    
    on_button_clicked = function(self)
        on_click_button(1)
    end,
}
local btnB = class.button:builder
{
    type = 'button',
    x = 100,
    y = 100,
    w = 60,
    h = 20,
    
    m_text = {
        type = 'text',
        x = 0,
        y = 0,
        w = 60,
        h = 20,
        text = '隐藏'
    },
    
    on_button_clicked = function(self)
        on_click_button(2)
    end,
}
```

其中 `on_button_clicked` 是点击按钮以后，在游戏内产生的回调方法。

可以在这里设置按钮的功能，此处我们调用 `on_click_button` 函数。

```lua
local function on_click_button(menu_id)
    if menu_id == 1 then
        panel:show() --显示
    elseif menu_id == 2 then
        panel:hide() --隐藏
    end
end
```

这样，就可以通过点击按钮来控制 `panel` 对象的显示与隐藏了。

倘若我们需要做菜单按钮，当玩家点击的时候会切换页面，而非显示/隐藏页面，可以做如下修改。

```lua
--修改按钮文本
btnA.m_text:set_text('页面1')
btnB.m_text:set_text('页面2')

--假设存在 page1 / page2 ，对应两个页面，类型为 panel
local page1 = ...
local page2 = ...

local function on_click_button(menu_id)
    if menu_id == 1 then
        page1:show()
        page2:hide()
    elseif menu_id == 2 then
        page1:hide()
        page2:show()
    end
end
```

通过上述修改，当玩家点击按钮的时候会切换页面，而非显示/隐藏页面。

如果我们需要更智能地去支持多个菜单按钮的切换，可以用如下写法：

```lua
--假设存在多个按钮
local btnA, btnB, btnC, btnD, ...
--与之对应，存在多个页面
local page1, page2, page3, page4, ...

--首先注册所有列表
local list_btn = { btnA, btnB, btnC, btnD, ... }
--所有页面
local list_page = { page1, page2, page3, page4, ... }

local function on_click_button(menu_id)
    local page = list_page[menu_id]
    if page then
        --显示目标页面
        page:show()
        
        --隐藏除了目标页面以外的其他页面
        for i = 1, #list_page do
            local other_page = list_page[i]
            if other_page ~= page then
                other_page:hide()
            end
        end
    end
end
```

可以批量的为所有按钮注册ID，并注册点击事件。

```lua
for i = 1, #list_btn do
    local btn = list_btn[i]
    btn.x_id = i
    btn.m_text:set_text('页面' .. i)
    btn.on_button_clicked = function(self)
        on_click_button(self.x_id)
    end
end
```

倘若我们需要在切换页面时刷新，可以为按钮被点击的事件添加刷新页面的逻辑。

```lua
local function refresh_page(menu_id)
    local page = list_page[menu_id]
    local btn = list_btn[menu_id]
    
    if page and btn then
        ... 在此处编写刷新逻辑 ...
    end
end

local function on_click_button(menu_id)
    local page = list_page[menu_id]
    if page then
        --显示目标页面
        page:show()
        
        --隐藏除了目标页面以外的其他页面
        for i = 1, #list_page do
            local other_page = list_page[i]
            if other_page ~= page then
                other_page:hide()
            end
        end
        
        --刷新目标页面
        refresh_page(menu_id)
    end
end
```
