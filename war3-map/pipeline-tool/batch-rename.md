# 批量重命名文件

nodejs

```js
const fs = require('fs');
const path = require('path');

// 配置参数
const source_dir = '.';
const source_files_pattern = /\.(mdx|mdl)$/i; // 匹配 .mdx 或 .mdl 文件
const target_name = 'NewModel_%d';

// 读取目录中的文件
fs.readdir(source_dir, (err, files) => {
  if (err) {
    console.error('读取目录出错:', err);
    return;
  }

  // 过滤出符合条件的文件
  const matchedFiles = files.filter(file => source_files_pattern.test(file));

  console.log(`找到 ${matchedFiles.length} 个匹配的文件`);

  // 重命名文件
  matchedFiles.forEach((file, index) => {
    const fileExt = path.extname(file); // 获取文件扩展名
    const newName = target_name.replace('%d', index + 1) + fileExt;
    const oldPath = path.join(source_dir, file);
    const newPath = path.join(source_dir, newName);

    fs.rename(oldPath, newPath, err => {
      if (err) {
        console.error(`重命名 ${file} 失败:`, err);
      } else {
        console.log(`${file} -> ${newName}`);
      }
    });
  });
});
```