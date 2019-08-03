# ES6
ES6巩固
### let const 块级作用域

### 解构赋值
```
  数组、对象、字符串
```

### 正则扩展(需学习)
```

```

### 字符串扩展
```
  计算长度：每两字节是一个长度;
  codePointAt()
  0xff
  for of
  padStart(2,'0') //补白 长度为2 长度不足2则以0开头补充长度
  padEnd(2,'0') // 日期月份选择
```

### 模版字符串
```
`${}`
```

#### 标签模板
```
  function abc(s, v1, v2) {
    return s + v1 + v2
  }
  let a = 'say';
  let b = 'hello'
  abc`baby,${a},${b}`
  console.log(abc`baby,${a},${b}`)
```

### 数值扩展
```
  Number.isFinite(15); //是否无穷
  Number.isNaN();
  Number.isInteger(); //是否整数
  Number.MAX_SAFE_INTEGER, Number.MIN_SAFE_INTEGER //常量 最大和最下
  Number.isSafeInteger() //是不是在上下最大最小值之间
  Math.trunc() //取整 4.9 => 4
  Math.sign() //判断正数 /负数/ 0  => ( 1, -1, 0, NaN)
  Math.cbrt() // 立方根 8 => 2
```

### 数组扩展
+ Array.from
```
  把伪数组/集合 转换为数组
  Array.from([1,2,3], function(item) {return item*2}) //function map
```
+ Array.of
```
  
```
+ copyWithin
  [1,3,5,7,9,11,13,15,17].copyWithin(0,3,7) // 从0开始替换 在3开始 7结束（不包括7）
+ find/findIndex
```
  find()找第一个的值
  findIndex()找第一个的index
```
+ fill
```
  [1,2,3].fill(7) //[7,7,7]
  [1,2,3,4].fill(7,1,2) // [1,7,7,4] 从1开始（包括1）到3结束（不包括3）
```
+ entries\keys\values
```
  keys() //返回下标
  values() //返回值
  entries() //返回键值

```
+ includes
```
  找寻存在返回布尔值
```
