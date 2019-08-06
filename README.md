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
```javascript
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
```javascript
  function abc(s, v1, v2) {
    return s + v1 + v2
  }
  let a = 'say';
  let b = 'hello'
  abc`baby,${a},${b}`
  console.log(abc`baby,${a},${b}`)
```

### 数值扩展
```javascript
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
```javascript
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
```javascript
  keys() //返回下标
  values() //返回值
  entries() //返回键值
```
+ includes
```
  找寻存在返回布尔值
```

### 函数扩展
##### 默认值
```
  function(x, y = 'world') {
    return y
  }
  //参数默认值后面只能跟赋值默认值的参数

```
##### 作用域
```
  let x = 'kill';
  function test (x, y=x) {
    console.log(x, y)
  }
  test('kill')
```

##### rest参数
```javascript
  function test1(...arg) {
    for(let v of arg) {
      console.log('rest',v)
    }
  }
  test(1,2,3,4,'a')
  console.log('a',[...1,2,4]) // a 1 2 4
```

**比对ES5中的argument 分析不同**

#### 箭头函数

```javascript
let arrow = v => v*2;
let arrow = () => 5;
```

#### 伪调用

```
提升性能：一个函数依赖于另一个函数的形式
```



### 对象扩展（Object）

#### 简洁表示法

```javascript
let o = 1;
let k = 2;
let obj = {
	o,k
}
let es6_method = {
	hello() {
		console.log('hello gaea')
	}
}
```

#### 属性表达式

```javascript
let a = 'b';
let es6_obj = {
	[a] = 'c'
}
```



#### 扩展运算符

```
let { a,b,...c } = {'aaa','bbb','ccc','ddd','eee','fff'}
```



#### 新增API

```javascript
console.log(Object.is('abc','abc') // 判断是否全等 相当于用 === 判断
Object.assign({'a':'b'},{'b':'c'}) // 浅拷贝 只拷贝自身 不拷贝继承属性和不可枚举的属性
entries()
let test = {k:123,0:456};
for (let [key,value] of Object.entries(test)) {
	console.log([key,value])
}
```

### Symbol

+ ##### 提供一个独一无二的值：声明的值永不相等

```javascript
// 声明的变量独一无二
let a1 = Symbol();
let a2 = Symbol();
console.log(a1 === a2) // false
// 如果要返回我们声明的值
let a3 = Symbol.for('a3') 
let a4 = Symbol.for('a3') 
console.log(a3 === a4 )
// a3相当于一个key值 当我们有该值时 for方法会去全局变量中找寻是否已声明 已声明则返回 否则声明该值
```



```javascript
let a = Symbol.for('abc');
let obj = {
	[a]:123,
	'abc':456,
	c: 789
};
console.log(obj)
for (let [key,value] of Object.entries(obj)) {
	console.log([key,value]) //获取不到通过Symbol声明的abc
}

Object.getOwnPropertySymbols(obj).forEach(function(item) {
	console.log(obj[item]) //获取通过Symbol声明的
})

Reflect.ownKeys(obj).forEach(item => {
	console.log(item,obj[item])
})
```

### set-map 数据结构

##### Set的用法：元素必须是唯一的

```javascript
let list = new Set();
list.add(5);
list.add(7);
console.log(list.size) // 2

let arr = [1,3,5,7];
let list1 = new Set(arr);
console.log(list.size) // 4
利用set的元素唯一性可以去重

let arrs = ['add','delete','clear','has'];
let list2 = new Set(arrs);

list2.has('add') //true
list2.delete('add')
list2.clear()
// key value值相同
```



##### WeakSet的用法

```javascript
let weakList = new WeakSet();
// 只支持对象
// 弱引用 不会检测该对象在其他地方有没有用过 不会与垃圾回收机制挂钩 不是拷贝 只是地址引用
let arg = {};
weakList.add(arg) // 不报错
weakList.add(2) // 报错
// 没有clear方法 不能遍历 没有size属性
```



##### Map的用法

```javascript
let map = new Map();
let arr = ['123'];
map.set(arr, 456) //添加元素
map.get(arr) //获取元素
```



```javascript
let map = new Map([['a',123],['b',456]]);
console.log('map args', map)
map.size // 2
map.delete('a')
map.clear()
// 遍历与set一样
```



##### WeakMap的用法

```javascript
let weakList = new WeakMap();
// 接收key值必须为对象
// 没有size属性 没有clear属性 不能遍历
```



### Proxy 和 Reflect

##### proxy 拦截/代理

```javascript
在代理层根据业务逻辑自定义
let obj = {
	time: '2019-08-04',
  name:'gaea',
  _id: 0810,
}
let monitor = new Proxy(obj, {
	get(target, key) {
  	return target[key].replace('2020','2019)
  },
	set(target, key, value) {
  	if(key == 'name') {
    	return target[key] = value
    } else {
    	return target[key]
    }
  },
  // 拦截 key in object 操作
  // 判断当前对象是否有某个属性
  has(target, key) {
  	if(key == 'name'){
    	return target[key]
    } else {
    	return false
    }
  },
  // 删除
  deleteProperty(target,key) {
  	if(key.indexOf('_') > -1) {
    	delete target[key]
      return true
    } else {
    	return target[key]
    }
  }
  // 拦截Object.keys, Object.getOwnPropertySymbols,Object.getOwnPropertNames
  ownKeys(target) {
  	return Object.keys(target).filter(item => item!= 'time')
  }
})
Reflect与Proxy用法基本一致
```

```javascript
// 实战：

function validator(target, validator) {
	return new Proxy(target, {
  	_validator: validator,
    set(target, key, value, proxy) {
    	if(target.hasOwnProperty(key)) {
      	let va = this._validator[key];
        if(!!va(value)) {
        	return Reflect.set(target, key, value, proxy)
        } else {
        	throw Error(`不能设置${key}到${value}`)
        }
      }
    }
  })
}

const personValidators = {
	name(val) {
  	return typeof val === 'string'
  },
  age(val) {
  	return typeof val === 'nubmer' && val > 18
  }
}

class Peroson {
	constructor(name,age) {
  	this.name = name;
    this.age = age;
    return validator(this,personValidators)
  }
}
const person = new Person('apollo',24);
person.name = 48 //error
person.name = 'gaea';
person.age = 23
```

### 类与对象

```javascript
class Perent() {
	constructor(name='gaea') {
  	this.name = name
  }
}
// 继承 extends
class child extends Parent() {
	constructor(name='apollo') {
  	super(name) 
    // 如果super括号为空，那么全部取父类的默认值：super放在第一行 如果定义子类独有的属性则定义放在super后
  }
}
```

```javascript
// getter setter
class Perent() {
	constructor(name='gaea') {
  	this.name = name
  }
  get heart() {
  	return 'my' + this.name
  }
  set heart(value) {
  	this.name = value
  }
}
let v = new Peroson();
v.herat
v.heart = 'is belong to gaea';
```

```javascript
 // 静态方法 
 class Perent() {
	constructor(name='gaea') {
  	this.name = name
  }
  static tell() {
  	console.log('hold on, i protect you)
  }
}
Person.tell()
// 静态属性
Person.peace = 'peaceful';
```

### Promise

```javascript
// Promise
// 基本定义
{
	let ajax = function(callback) {
  	console.log('inplement1');
    setTimeout(function(){
    	callback && callback()
    },1000)
  }
  ajax(function(){
  	console.log('inplement2')
  })
}

{
	let ajax = function() {
  	console.log('inplement3')
    return new Pormise(function(resolve,reject){
    	setTimeout(function(){
        resolve()
      },1000)
    })
  }
  ajax().then(function(){
  	console.log('inplement4')
    return new Promise(function(resolve, reject){
    	setTimeout(function(){
      	resolve()
      }, 2000)
    })
  })
}
```

##### Promise.all  &&  Promise.race

```javascript
function loadImg(src) {
	return new Pormise((resolve, reject)) => {
  	let img = document.createElement('img');
    img.src = src;
    img.onload = function(){
    	resolve(img)
    };
    img.onerror = function(err){
    	reject(err)
    }
  }
}
function showImgs(imgs) {
	imgs.forEach((img) => {
  	document.body.append(img)
  }
}
// 三张图片全部加载完毕再执行show
Promise.all([
	loadImg('a.png'),
	loadImg('b.png'),
	loadImg('c.png'),
]).then(showImgs)
// 一张图片加载完毕就执行show
Promise.race([
	loadImg('a.png'),
	loadImg('b.png'),
	loadImg('c.png'),
]).then(showImgs)

```

### Iterator  &&  fro ... of

```javascript
// for of 就是利用iterator的特性来对数组/对象进行循环调用
let arr = ['hello','world'];
let map = arr[Symbol.iterator]();
console.log(map.next());
console.log(map.next());
console.log(map.next());

let obj = {
	start: [1,3,5],
  end: [7, 9, 11],
  [Symbol.interator](){
  	let self = this;
    let index = 0;
    let arr = self.start.concat(self.end);
    let len = arr.length;
    return {
    	next() {
      	if(index< len) {
        	return {
          	value: arr[index++],
            done: false
          }
        } else {
        	return {
          	value: arr[index++],
            done: true
          }
        }
      }
    }
  }
}
for (let key of obj) {
	console.log(key)
}

```

### Generator

```javascript
// 异步编程的一种解决方案
// 基本定义
let tell = function* () {
	yield:'a',
  yield:'b',
	return: 'c'
}
let k = tell();
console.log(k.next()) // {value: a,done:false}
console.log(k.next()) // {value: b,done:false}
console.log(k.next()) // {value: c,done: true}
console.log(k.next()) // {value:undefined,done:true}
// 遇到yield则停住不执行 执行yield之前的; 执行next()开始执行第一个yield
```

```javascript
// Generator是一个使函数内部看上去类似于异步的操作过程 
// Generator就是一个遍历器生成的函数 可以直接赋值给Symbol.intraotr接口上
// 任意一个对象的interator接口都是在Symbol.interator属性上
{
	let obj = {};
  obj[Symbol.iterator]= function* (){
  	yield 1;
    yield 2;
    yield 3;
  }
  for(let value of obj) {
  	console.log(value)
  }
}
```

```javascript
// 状态机
let state = function* () {
	while(1) {
  	yield 'a';
    yield 'b';
    yield 'c';
  }
}
let status = state();
console.log(status.next()); //a
console.log(status.next()); //b
console.log(status.next()); //c
console.log(status.next()); //a
console.log(status.next()); //b
console.log(status.next()); //c
```

### async await(Generator语法糖)

```javascript
let state = async function () {
	while(1) {
  	await 'a';
    await 'b';
    await 'c';
  }
}
let status = state();
console.log(status.next()); //a
console.log(status.next()); //b
console.log(status.next()); //c
console.log(status.next()); //a
console.log(status.next()); //b
console.log(status.next()); //c
```

##### 抽奖逻辑

```javascript
let draw = function(count) {
	// 具体抽奖逻辑
  console.log(`剩余${count}次`);
}
let residue = function* (count) {
	while(count>0){
  	count--;
    yield draw(count)
  }
}

let star = residue(5);
let btn = document.createElement('button');
btn.id = 'start';
btn.textContent = '抽奖';
document.body.appendChild(btn);
document.getELementById('start').addEventListener('click',function(){
	star.next();
},false)
```

```javascript
// 长轮询
let ajax = function* (){
	yield new Promise(function(resolve,reject){
  	setTimeout(function () {
    	resolve({code: 0})
    }, 200)
  })
}

let pull = function() {
	let generator = ajax();
  let step = genrator.next();
  step.value.then(function(d){
  	if(d.code!=0) {
    	setTimeout(function() {
      	console.log('waiting');
        pull()
      },200)
    } else {
    	console.log(d)
    }
  })
}
pull()
```



















































