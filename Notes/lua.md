# Learn lua

## 基础

### 注释和nil

```lua
print('Hello World')

-- 单行注释

--[[
多行注释
多行注释
--]]

-- 删除一个变量
b = 10
b = nil
print(b)
```

### 变量

```lua
local a = 1 -- 局部变量
b = 2   -- 全局变量
c,d = 1,2   -- 多个全局变量同时赋值
print(c,d)
```

### 数值型

```lua
a = 0x11    -- 十六进制
b = 2e10    -- 科学计数法
print(a)
```

### 运算符

```lua
a = 1
b = 2
print(a+b)
print(10^5)
print(1<<3)
```

### 字符串

```lua
a = "abc"
b = 'abc'
-- 转义字符
c = 'a\nd'
-- 多行字符串
d = [[
123
456
789
]]
e = a..b    -- 字符串拼接
-- 数值转为字符串
f = tostring(10)
-- 字符串转为数值
g = tonumber('10')

print(a,b,c,d,e)

print(type(f))
print(type(g))
-- 查看字符串长度
print(#a)
```


### 字符串2
```lua
s = string.char(0x30,0x31,0x32)
n = string.byte(s,2)
print(s)
print(n,#s)
```

### 函数

```lua
function No(a,b,c)
    return a,b
end

local i,j = No(1,2)

print(i)
print(j)
```

### 数组1

```lua
a = {1,'a',{},true}
a[5] = 123

--[[
print(a[1])
print(a[2])
print(a[3])
print(a[4])
print(a[5])
--]]

--[[
    插入一个元素
        参数：
            1.变量
            2.指定插入的位置
            3.插入的内容
--]]
table.insert(a,6,'b')
print(a[6])     -- b

--[[
    移除元素
--]]
local s = table.remove(a,1)
print(a[1])     -- a
print(s)        -- 1

print(#a)
```

### 数组2

```lua
a = {
    a = 1,
    b = 'b',
    c = function()

    end,
    d = 123
}
a['abc'] = 456
print(a.a,a.b,a.c,a.d)
print(a.abc)
```

### 表_G

```lua
-- 全局变量都在_G里面
a = 123
print(_G["a"])
```

### 真和假

```lua
a = true
b = false

print(1>2)
print(1<2)
print(1>=2)
print(1<=2)
print(1==2)
print(1~=2)

print(a and b)  -- 与
print(a or b)   -- 或
print(not a)    -- 非

-- 短值判断语句
c = nil -- 假
d = 0   -- 真
print(d > 10 and 'yes' or 'no')
```

### 分支判断语句

```lua
if 1>10 then
    print('1>10')
elseif 1 < 10 then
    print('1<10')
else
    print('no')
end

if 0 then
    print('0 is true!')
end
```

### for循环

```lua
--[[
    for参数：
        1.初始循环值
        2.循环的结束值
        3.步长
--]]
for i=1,10,2 do
    print(i)
end

-- 倒序

for a=10,1,-1 do
    print(a)
    if a == 5 then break end
end
```

### while循环

```lua
--[[
    while循环
--]]

local n = 10
while n > 1 do
    if n == 5 then break end
    print(n)
    n = n - 1   -- 不支持使用n--
end
```

## 进阶

### require

```lua
require('hello')    -- 调用当前目录的hello.lua
require('test.a')   -- 调用当前目录下的test目录下的a.lua
```

### 制作库
```lua
local Noi = {}

function Noi.sayName() 
    print('Hello World!')
end

return Noi
```
