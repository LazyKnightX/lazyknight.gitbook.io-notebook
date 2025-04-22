# 装饰物物编生成

## nodejs 生成 doodad.ini 数据

自行填写代码中 `list` 的参数来生成数据。

```javascript
const fs = require('fs');

const tpl = `[AAA]
_parent = "ZOrt"
-- 名字
Name = "BBB"
-- 迷雾中显示动画
animInFog = 1
-- 类别
category = "S"
-- 默认比例
defScale = 1.0
-- 模型文件
file = "BBB"
-- 样式总数
numVar = 1
-- 路径纹理
pathTex = ""
-- 地形设置
tilesets = "*"
`;

let list = [
    { gid: "D000", name: "mx_yy_00.mdl" },
    { gid: "D001", name: "mx_yy_01.mdl" },
    { gid: "D002", name: "mx_yy_02.mdl" },
    { gid: "D003", name: "mx_yy_03.mdl" },
    { gid: "D004", name: "mx_yy_04.mdl" },
    { gid: "D005", name: "mx_yy_05.mdl" },
    { gid: "D006", name: "mx_yy_06.mdl" },
    { gid: "D007", name: "mx_yy_07.mdl" },
    { gid: "D008", name: "mx_yy_08.mdl" },
    { gid: "D009", name: "mx_yy_09.mdl" },
    { gid: "D00A", name: "mx_yy_10.mdl" },
    { gid: "D00B", name: "mx_yy_11.mdl" },
    { gid: "D00C", name: "mx_yy_12.mdl" },
    { gid: "D00D", name: "mx_yy_13.mdl" },
    { gid: "D00E", name: "mx_yy_14.mdl" },
    { gid: "D00F", name: "mx_yy_15.mdl" },
];

// 创建一个空字符串来存储所有内容
let allContent = '';

// 为每个列表项生成内容并添加到 allContent
list.forEach(item => {
    // 替换模板中的 AAA 和 BBB
    let content = tpl.replace(/\[AAA\]/g, `[${item.gid}]`)
                     .replace(/BBB/g, item.name);

    // 添加到总内容
    allContent += content + '\n';
});

// 写入单个文件
fs.writeFileSync('combined_output.txt', allContent);
console.log('已生成合并文件: combined_output.txt');
```

## 手动填写

填写后把 ` | ` 移除并换行。

```plaintext
[D000] | _parent = "ZPsh" | Name = "导入模型-1" | file = "自定义模型路径-1.mdl" | maxScale = 5. | minScale = 0.1 | numVar = 1
[D001] | _parent = "ZPsh" | Name = "导入模型-2" | file = "自定义模型路径-2.mdl" | maxScale = 5. | minScale = 0.1 | numVar = 1
[D002] | _parent = "ZPsh" | Name = "导入模型-3" | file = "自定义模型路径-3.mdl" | maxScale = 5. | minScale = 0.1 | numVar = 1
[D003] | _parent = "ZPsh" | Name = "导入模型-4" | file = "自定义模型路径-4.mdl" | maxScale = 5. | minScale = 0.1 | numVar = 1
[D004] | _parent = "ZPsh" | Name = "导入模型-5" | file = "自定义模型路径-5.mdl" | maxScale = 5. | minScale = 0.1 | numVar = 1
[D005] | _parent = "ZPsh" | Name = "导入模型-6" | file = "自定义模型路径-6.mdl" | maxScale = 5. | minScale = 0.1 | numVar = 1
[D006] | _parent = "ZPsh" | Name = "导入模型-7" | file = "自定义模型路径-7.mdl" | maxScale = 5. | minScale = 0.1 | numVar = 1
[D007] | _parent = "ZPsh" | Name = "导入模型-8" | file = "自定义模型路径-8.mdl" | maxScale = 5. | minScale = 0.1 | numVar = 1
[D008] | _parent = "ZPsh" | Name = "导入模型-9" | file = "自定义模型路径-9.mdl" | maxScale = 5. | minScale = 0.1 | numVar = 1
[D009] | _parent = "ZPsh" | Name = "导入模型-10" | file = "自定义模型路径-10.mdl" | maxScale = 5. | minScale = 0.1 | numVar = 1
```
