# 字符串转魔兽ID

![](/files/img/misc_01.png)

通过 `string.unpack(">I4", "u000")` 可以将字符串 `"u000"` 转换为魔兽整数ID，对应到Jass中的写法是 `'u000'` 。

要注意**单双引号的差别**，以及单双引号在Lua和Jass中**不同的含义**。

也可以使用 `FourCC` 函数来等效替代。

## 原理

魔兽里， `'u000'` 这样的写法实际上对应的是一串整数。
在Lua中，想要让输入的字符串 `"u000"` 与Jass中的写法 `'u000'` 相同，需要使用 `string.unpack` 函数。
