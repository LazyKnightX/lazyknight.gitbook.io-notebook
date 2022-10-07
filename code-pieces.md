# Code Pieces

pieces of code here.

# A

## Build Game Unit

```lua
local MainQuest = {}
MainQuest.Units = {}

local u_enemy = CreateUnit(uid, GetPlayerPoint(player, 'MainEnemyPoint'), 270, 'Enemy')

function GetPlayerPoint(player, label)
    local pid = player:GetID()
    if label == 'MainEnemyPoint' then
        return {{-512,0}, {512,0}, {0,512}, {0,-512}}[pid]
    end
end

function CreateUnit(uid, point, face, type)
    local unit = ... stuffs here ...
    Matrix.SetupUnitPower(u, type)
    return unit
end

function Matrix.CalcUnitPower(u, type)
    local info = {}
    if type == 'Enemy' then
        info.ATK = G_DIFFICULT * G_CHAPTER * 300
        info.DEF = G_DIFFICULT * G_CHAPTER * 50
        info.HP = G_DIFFICULT * 1000 + G_CHAPTER * 200
    end
    return info
end

function Matrix.AssignUnitPower(u, info)
    if info.ATK then u:SetAttr('ATK', info.ATK) end
    if info.DEF then u:SetAttr('DEF', info.DEF) end
    if info.HP then u:SetAttr('HP', info.HP) end
    if info.MP then u:SetAttr('MP', info.MP) end
    if info.SPD then u:SetAttr('SPD', info.SPD) end
    if info.RNG then u:SetAttr('RNG', info.RNG) end
    if info.SIGHT then u:SetAttr('SIGHT', info.SIGHT) end
end

function Matrix.SetupUnitPower(u, type)
    local info = Matrix.CalcUnitPower(u, type)
    Matrix.AssignUnitPower(info)
end
```
