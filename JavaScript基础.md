# 一、类型、值、变量

## 1.类型

### ①原始类型   

​            -->    不可修改  

- 数值

- 文本字符串

- 布尔值

- null                                     【特殊值】没有属性与方法

- undefined                         【特殊值】没有属性与方法

- <p style="color:#1e3e8c">Symbol（符号）     es6新增【特殊值】</p>

### ②对象类型    

​             -->     可修改  

- <p style="color:#1e3e8c">对象：任何不是原始类型的值都是对象，对象是属性的集合</p>

  - Set对象 —— 一组值的集合
  - Map对象 —— 键与值的映射
  - 各种”定型数组（typed array）”类型 —— 便于对字节数组和其他二进制数据进行操作
  - RegExp类型 —— 文本模式，实现对字符串的复杂匹配、搜索和替换操作
  - Date类型 —— 日期和时间，支持基本的日期计算
  - Error及其子类型 —— 代码运行期间可能发生的错误

- **函数**和**类**也是特殊的对象

- 数组（特殊对象）—— 一个数字值的有序集合

## 2.数值

Number —— 用于表示整数和近似实数

- 整数字面量
- 浮点字面量
- 计算
  - Math对象提供的方法
    - Math.pow(a,b)  	a的b次方
    - 取整
      - Math.round()
      - Math.ceil()
      - Math.floor()
    - Math.abs()            绝对值
    - Math.random()    随机数
    - Math.sqrt()           平方根

## 3.文本

String —— 16位值的不可修改的有序序列，其中每一个值表示一个Unicode字符【**字符串是不可修改的**】

- 转义序列 \ —— 可以在 ' 前加上 \ 进行转义，则 ' 不表示字符串结束，而表示撇号
  - \n 	换行符
  - \b     退格符
  - \t      水平制表符
  - \v      垂直制表符
  - \r       回车符

- 字符串的相关API
  - s.substring(1,4)		//获取第2-4个字符
  - s.slice(1,4)                 //获取第2-4个字符
  - s.slice(-3)                   //获取最后3个字符
  - s.split(",")                   //从定界符出拆分字符串
  - s.indexOf("a")           //搜索第一个字母a在字符串中的位置
  - s.indexOf("a",3)        //搜索位置3后面的第一个字母a在字符串中的位置
  - s.replace("a","b")      //b替换a
  - s.charAt()                   //访问第几个字符
  - s.trim()                       //删除空格

## 4.布尔值

- 假值 —— false、null、undefined、0、-0、NaN、""
- 真值 —— 除了假值以外的值，包括所有的对象

## 5.null与undefined

​	都可以当成false使用，没有属性与方法

- null
  - 用**typeof操作符返回'object'**，因此null可以看成一种特殊对象，表示“没有对象”

- undefined
  - 更深层次的不存在
  - 预定义的全局常量
  - typeof返回值为'undefined'，表示这个值是该特殊类型的唯一成员

## 6.符号Symbol

- Symbol( ) —— 永远不会返回相同的值，即使传参一样也不会
- Symbol.for( ) —— 接收一个字符串参数，参数相同时会始终返回相同的值

## 7.不可修改的原始值、可修改的对象引用

- **原始值**是不可修改的 —— 例如字符串在修改某一个字符后，实际上是返回一个新的字符串【按值比较】
- **对象**（引用类型）是可修改的 —— 即使两个对象拥有完全相同的属性与方法，都不相等

## 8.变量声明与赋值

- 变量 —— let
  - 一条let语句能够同时声明多个变量	//let i,sum;
  - 声明变量的同时为变量赋初始值
    - 若不指定初始值，变量也会声明，但赋值之前是undefined（不提倡）

- 常量 —— const
  - 把一个值永久地赋给一个名字
  
  - 声明时必须赋初始值
  
  - 常量的值不能改变
  
    

### 	⚠️let、const注意点

```text
①块级作用域 —— 在其声明的花括号{ }作用域内

②重复声明 —— 同一作用域内使用多个let或const声明同一个名字是语法错误

③声明与类型 —— 变量的声明与值的类型无关
```



### 	⚠️**var**关键字与**let**的区别

- 函数作用域 —— var声明的变量不具备块级作用域

  - 作用域仅限于包含函数的函数体

  - 若在函数体外部，则会声明全局变量 —— 即全局对象的属性，全局对象可以通过globalThis引用

    【let和const声明的全局变量和常量不是全局对象的属性】

- 重复声明 —— var多次声明同名变量是合法的
- 作用域提升 —— var声明变量时，该声明会提升的函数顶部，但初始化不会，因此在初始化之前，变量的值可能是undefined

# 二、表达式与操作符

- 主表达式——最简单的表达式称为主表达式

  - 常量或字面量（字面量是可以直接嵌入在程序中的常量值）

  - 保留字

  - 变量、常量、全局对象属性的引用

- 数组初始化程序 [ ]
- 对象初始化程序 { }
- 函数定义表达式 function ( ) { }
- 属性访问表达式——访问对象属性或数组元素
  - expression . identifier
  - expression [ expression ]

- 【ES2020】条件式属性访问表达式 —— 若属性访问前的表达式为null或undefined会抛出TypeError，因此可以用 ?. 或 ?.[ ] 防止这种错误的发生
- 调用表达式 —— 调用函数或方法
  - 如果函数使用了return返回一个值，该值就是调用表达式的值；否则调用表达式的值为undefined

- 【ES2020】条件调用表达式 —— 检查左侧的值是不是null或undefined，不会验证该值是不是函数 ?.( )
- 对象创建表达式（构造函数）——创建一个新对象并调用一个函数 new Object（ ），值为新创建的对象

- 算术表达式
  - +操作符优先字符串拼接
- 关系表达式
  - ⚠️NaN===NaN	false	如果要检查某个值x是不是NaN，可以使用x !==  x 或 全局isNaN( )函数
  - Instanceof 操作符
    - 左侧是对象，右侧是对象类的标识——**左侧对象是右侧类的实例**时求值为true
    - ⚠️所有对象都是Object的实例

- 逻辑表达式
  - ⚠️若想要取得任何值x对应的布尔值，只要对x进行两次取反：! ! x
  - && 及 || “短路”行为 ——||当第一个值为真时就会短路，直接返回真值，不再对右侧表达式求值

- 赋值表达式
- 求值表达式

# 三、语句

### ①分支语句

- if else  /  else if
- switch
  - 每一个case语句都有一个break，同时default语句可以出现在switch语句体的任意位置

### ②循环语句

- while / do while
  - 区别：do while的循环表达式在语句底部而不是顶部，也就意味着循环体至少执行一次

- for
  - for语句中的三个表达式中任何一个都可以省略

#### 		⚠️for/of 与 for/in的区别

```text
▪︎for / of【ES6】—— 枚举可迭代对象的值               可迭代对象【数组、字符串、集合、映射】
  ▫︎ 对象（默认）是不可迭代的
    - 迭代对象的属性名——for / in 或 基于Object.keys()          返回值为属性名数组
    - 迭代对象的属性值——基于Object.values()                    返回值为属性值数组
    - 对象的键与对象的值——基于Object.entries()		              返回值为可枚举属性的键值对的对象(key/value)

▪︎for / in —— 枚举对象的属性名
  ▫︎ ⚠️操作数组时，基本上只会用 for / of 而不会用 for / in
```



### ③跳转语句 

​								—— break、continue、return、yield、throw(配合 try / catch / finally 使用)

- label语句标签 —— 前置一个标识符及冒号，为任何语句加上标签
  - break、continue是唯一使用语句标签的语句

- break —— 退出最内部循环、switch或有名字的闭合语句
- continue —— 不退出循环，开始最内部循环或命名循环的下一次迭代，只能在循环体内部使用
- return —— 指定函数调用的返回值，否则函数的调用返回值为undefined，只能在循环体内部使用

### ④声明 

​					—— const、let、var、function、class、import、export

#### 		function 与 class 的区别

```text
function —— 无论在什么地方声明函数，**函数都会被“提升”**，因此可以在函数之上调用函数
class类 —— **类不会被“提升”**，因此不能在声明之前使用类
```

# 四、对象

## 1.简介

- 对象是一种**复合值**，允许按照名字存储和获取这些值。对象是一个属性的无序集合，每个属性都有名字和值。
- 对象可以从其他对象**继承属性**，这个其他对象就是“原型”
- 对象是**动态**的，可以动态添加和删除属性
- 对象的修改是**按引用操作**
- **区分**<u>直接定义在对象上的属性（自有属性）</u>和<u>那些从原型对象上继承的属性</u>很重要
- 除名字和值外，属性还有**三个属性特性**（默认false）
  - writable （可写）特性 —— 指定是否可以设置属性的值
  - enumerable （可枚举）特性 —— 指定是否可以在for/in循环中返回属性的名字
  - configurable（可配置）特性 —— 指定是否可以删除属性，以及是否可以修改其特性

## 2.创建对象

### ①使用**对象字面量**创建

​      【原型为Object.prototype】

### ②使用**new**创建 

​        —— new关键字后跟着一个函数调用（构造函数）【原型为构造函数的prototype】

- 内置构造函数
  - new Object( )      //空对象										【原型为Object.prototype】
  - new Array( )        //空数组                                        【原型为Array.prototype】
  - new Date( )         //表示当前时间的日期对象         【原型为Date.prototype】
  - new Map( )          //映射对象，存储键/值映射       【原型为Map.prototype】

### ③使用**Object.create( )**创建 

​		—— 使用第一个参数作为新对象的**原型**【可以以任意原型创建新对象】

- 传入null可以创建没有原型的新对象（不会继承任何属性和方法）

- 传入Object.prototype可以创建一个普通的空对象

  

<p style="color:#cd5a4b;font-size:20px">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;🌟原型</p>

```text
几乎每个对象都有原型，但大多数对象没有prototype属性 （只有函数对象有prototype属性）
							—— Object.prototype是为数不多没有原型的对象，不继承任何属性
```

## 3.查询和设置属性

<p style="color:#1e3e8c">.标识符</p>

<p style="color:#1e3e8c">["字符串"]</p>

- 继承 —— 对象有一组“自有属性”，同时也从原型上继承一组属性

  - 假设为对象o的x属性赋值，如果o有一个名为x的自有属性，那么就会修改原有的x的值

    ​                                               如果没有名为x的自有属性，则会在o上创建一个名为x的新属性

    ​                                               如果o之前就继承了属性x，那么继承的x属性会被新创建的同名属性隐藏（覆盖）                                               

  - 🌟js重要特性：**查询属性时会用到原型链，设置属性时不影响原型链**

- 属性访问错误
  - 如果o自有属性和继承属性都没有找到属性x，则o.x的值为undefined
  - 如果查询不存在对象（如null、undefined）的属性，会跑出错误TypeError
  - 如果 null. 或 undefined. 访问属性，会失败；在null和undefined上设置属性也会导致TypeError

## 4.删除属性

delete操作符 —— 从对象中移除属性【不是操作属性的值，而是操作属性本身】

- 只删除自有属性，不删除继承属性
- 不会删除configurable特性为false的属性

## 5.测试属性

- **in操作符**
  - 属性名   in   对象 —— 如果对象包含相应名字的自有属性或继承属性，返回true

- **hasOwnProperty( )**
  - 测试对象是否有给定名字的自有属性 —— 对于继承的属性，返回false
  - **propertyIsEnumerable( )** —— 自有属性且enumerable特性为true，则返回true

## 6.枚举属性

遍历或获取对象的所有属性

- for / in —— 遍历所有可枚举属性的属性名
- for / of —— 先获取对象的所有属性名的数组，再用for/of遍历该数组
  -  获取属性名数组的函数【ES6】
    - Object.keys() —— 可枚举 自有属性名
    - Object.getOwnPropertyNames() —— 自有属性名（可枚举和不可枚举都有）
    - Object.getOwnPropertySymbols() —— 符号的自有属性（可枚举和不可枚举都有）
    - Reflect.ownKeys() —— 所有属性名（包括可枚举和不可枚举属性、字符串属性和符号属性）

<p style="color:#cd5a4b;font-size:20px">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;属性枚举的顺序</p>

```text
-【上述ES6方法】
①先列出名字为非负整数的字符串属性              【按数值从小到大】
②再列出类数组索引的所有属性                   【按数值从小到大】
③再列出所有剩下的字符串名字的属性              【按添加到对象的先后顺序】
④最后列出名字为符号对象的属性                 【按添加到对象的先后顺序】

- for/in 循环
先按照上述枚举顺序枚举自有属性，再沿原型链上溯，以同样的顺序枚举每个原型对象的属性（若已有同名属性被枚举过则不会再枚举该属性）
```

## 7.扩展对象

把一个对象的属性复制到另一个对象上

```js
let target = {x:1}, source = {y:2, z:3};
for(let key of Object.keys(source)) {
  target[key] = source[key];
}
// target = {x:1, y:2, z:3}
```

- Object.assign( targetObj , obj )  —— obj里的属性会**覆盖**掉targetObj里的**同名属性**

- 手写一个只复制不存在属性的方法

  ```js
  function merge(target,...sources) {
    for(let source of sources) {
      for(let key in source) {
        if(!key in target) {
          target[key] = source[key];
        }
      }
    }
    return target;
  }
  ```

<p style="color:#cd5a4b;font-size:20px">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;上述两个方法的区别</p>

```js
Object.assign({x:1},{x:2,y:2},{y:3,z:4})   //{x:2,y:3,z:4}  会覆盖掉同名属性
merge({x:1},{x:2,y:2},{y:3,z:4})           //{x:1,y:2,z:4}  只会复制不存在属性
```

## 8.序列化对象

serialization对象序列化 【JSON（Javasrcipt Object Notation）指 JavaScript对象表示法】

- JSON.stringfy( )      序列化 —— 将对象转化为字符串形式对象【**只序列化对象的可枚举自有属性**】
- JSON.parse( )          恢复 —— 将字符串形式对象转化为对象类型

```text
可以序列化和恢复：
							对象、数组、字符串、有限数值、true、false、null
被序列化为null：						
							NAN、Infinity、-Infinity会被序列化为null
能被序列化，但不能恢复为对象：
							           Date对象
不能被序列化或恢复：
								函数、RegExp、Error对象、undefined
```

# 五、数组

```text
数组是一种基础数据类型
▫︎ 数组是无类型限制的
	- 即创建数组时无需声明固定大小，也无需在大小变化时重新分配空间
	
	◦ 稀疏数组 —— 元素不一定具有连续索引，中间可能有空隙（连续包含多个逗号，	且逗号之间没有值）
				例：let arr = [,,]   //这个数组的长度为2而不是3
	◦ 【ES6新增】定型数组 —— 具有固定长度和固定的数值元素类型
```

## 1.创建数组

- 数组字面量  [ ]
- 扩展操作符  ...     =>  适用于任何**可迭代对象**

- Array( )构造函数             let a = new Array( ); 
  - ①不传参                                       创建一个没有元素的空数组，等价于数组字面量[ ]
  - ②传一个参数（指定长度）        创建一个指定长度的数组，会预先为数组分配空间
  - ③传多个参数或非数值参数        传入的参数会变成新数组的元素         

- 【ES6】Array.of( )

  - Array( )构造函数无法创建只包含**一个参数**的数组，Array.of( )能够解决这个问题
  - Array.of( )可以使用其参数值（无论多少个）做为数组元素创建并返回新数组

  ```js
  Array.of();//返回[]
  Array.of(10);//返回[10]
  Array.of(1,2,3);//返回[1,2,3]
  ```

- 【ES6】Array.from( )

  - 第一个参数 —— 可迭代对象或类数组对象
    - 能够**将类数组对象转换成真正的数组**       

  - 第二个参数 —— 传入一个函数（源对象的每个元素都会传入这个函数，这个函数的返回值将代替原始值称为新数组元素）

## 2.读写数组元素

使用**[ ]**操作符访问数组元素

​					—— 数组是一个特殊对象，访问数组元素类似于访问对象属性，只不过使用的是**非负整数**作为属性名

​				⚠️注意（如果使用<u>负数或非整数值</u>访问数组，[ ]里的数值会转为字符串，会被当成<u>常规的对象属性</u>，该字符串会作为属性名）

- 查找不存在的属性则会返回undefined

## 3.稀疏数组

length属性会大于元素个数，被省略的元素是不存在的

- 使用Array( )构造函数创建
- 直接给大于当前数组length的数组索引赋值
- 使用delete操作符创建

## 4.添加和删除数组元素

- 给新索引赋值
- push( )              在数组末尾添加一个或多个元素
- pop( )                删除数组最后一个元素并返回该元素，同时数组长度减1
- unshift( )          在数组开头插入值
- shift( )               删除并返回数组的第一个元素，同时数组长度减1
- delete操作符   删除数组元素，但不影响数组长度，并给该其赋undefined值（变成稀疏数组）
- 将数组length属性设置成一个新的长度值
- splice( )方法     能够插入、删除或替换数组元素

## 5.迭代数组

- for / of 最简单的方法 —— 返回每一个数组元素（不存在的元素则返回undefined）

  ```js
  let letters = [..."Hello world"];
  let str = "";
  for(let letter of letters) {
    str += letter;
  }
  console.log(str);//"Hello world"
  ```

- entries( )方法 + 解构赋值 —— 返回一个数组的迭代对象，包含数组的键值对(key/value)

  ```js
  let everyother = "";
  for(let [index,letter] of letters.entries()) {
    if(index %2 === 0) everyother += letter;
  }
  console.log(everyother);//"Hlowrd"
  ```

- forEach( ) —— 数组提供的自身迭代的函数式方法

  ```js
  let uppercase = "";
  letters.forEach(letter => {
    uppercase += letter.toUpperCase();
  })
  console.log(uppercase);//"HELLO WORLD"
  ```

  - 参数为一个**箭头函数**
    - 函数第一个参数为：数组元素
    - 函数第二个参数为：索引值
    - 函数的第三个参数为：当前数组

  - 🌟能够感知到稀疏数组，不会对没有的元素数组调用函数

-  for循环

## 6.数组方法

### ①迭代器方法

​	                   【第一个参数：函数（一般是箭头函数） => ①元素值 ②索引 ③数组本身】

​				       【第二个参数（可选）：作为第一个参数传入函数内部的this值】

​             —— 按照顺序将每个元素调用一次函数（不会对不存在的元素调用函数）

- forEach( ) —— 迭代数组的每个元素，并对每个元素调用一次指定的函数

  ```js
  let data = [1,2,3,4,5], sum = 0;
  //计算数组之和
  data.forEach(val => {sum += val});//sum = 15
  
  //递增每个元素的值
  data.forEach(function(v,i,a) {a[i] = v + 1});//data = [2,3,4,5,6]
  ```

  ⚠️forEach( )并没有提供提前终止迭代的方法

- map( ) —— 把调用它的数组的每个元素分别传给我们指定的函数，**《返回》**这个函数的返回值构成的**《新数组》**   

  - 返回一个新数组，并不修改原数组；
  - 若原数组是稀疏数组，为定义的值不会调用该函数，但返回数组会与原始数组一样稀疏；长度相同，缺失元素相同。

  ```js
  let a = [1,2,3];
  a.map(x => x*x);//[1,4,9]		
  ```

- filter( )  【参数：断言函数 => 返回true或false的函数】

  - 返回一个新数组（结果为true的数组成员）
  - 返回的数组始终是稠密的，会清理掉稀疏数组中的空隙

  ```js
  let a = [5,4,3,2,1];
  a.filter(x => x<3);//[2,1]
  a.filter((x,i) => i%2 === 0);//[5,3,1]
  ```

- find( )与findIndex( ) —— 与filter( )类似，区别为在**断言函数找到第一个满足条件的元素时停止迭代**

  - 返回值

    find( ) 返回匹配的元素         findIndex( )返回匹配元素的索引

  - 若没有找到匹配的元素

    find( ) 返回undefined         findIndex( )返回-1

  ```js
  let a = [1,2,3,4,5];
  a.findIndex(x => x===3);//2
  a.findIndex(x => x<0);//-1
  a.find(x => x%5 === 0);//5
  a.find(x => x%7 === 0);//undefined
  ```

- every( ) 和 some( ) —— 数组断言方法，**返回值为true或false**   

  - every( ) —— 在断言函数对数组所有元素都返回true时才返回true

    ```js
    let a = [1,2,3,4,5];
    a.every(x => x < 10);//true
    a.every(x => x %2 === 0);//false
    ```

  - some( ) —— 只要有一个数组元素返回true就返回true，只有全部元素都返回false才返回false

    ```js
    let a = [1,2,3,4,5];
    a.some(x => x%2 === 0);//true
    a.some(isNaN);//false
    ```

    <p style="color:#68d74b; font-size:16px">⚠️every( )和some( )知道什么时候要停止迭代数组</p>

    -> every( ) 在第一次返回false时停止迭代，只有全部断言都返回true时才会遍历数组

    -> some( ) 在第一次返回true时停止迭代，只有全部断言都返回false时才会遍历数组

    

- reduce( ) 和 reduceRight( ) —— 使用指定函**数归并数组元素**，最终产生一个值

  - reduce( )

  ​            【第一个参数：执行归并操作的函数 =>  ① 目前为止归并操作的累积结果  ② currentValue ③ currentIndex ④ arr】

  ​            【第二个参数（可选）：初始值（作为函数的第一个参数；若没有传该参数，则会使用数组的第一个元素作为初始值）】

  ```js
  let a = [1,2,3,4,5];
  a.reduce((x,y) => x+y,0);//15    所有值之和
  a.reduce((x,y) => x*y,1);//120   所有值之积
  a.reduce((x,y) => (x>y)?x:y);//5 最大值
  ```

  - reduceRight( )      与reduce( )类似，但**从右向左处理数组**

#### 	⚠️迭代器方法的区别

```text
▪︎forEach((val,index,arr) => {}) 
	-只接收一个参数：函数
	-没有返回值，每个数组元素都调用一次该函数
▪︎map((val,index,arr) => {})
	-接收一个参数，函数
	-返回一个新数组，不会修改原数组【稀疏数组也会返回，空隙相同】
▪︎filter((val,index,arr) => {},this)
	-接收两个参数
			①断言函数
			②（可选）this，作为断言函数的this的值
	-返回一个新数组，包括满足条件的数组元素【返回的数组是稠密的，即稀疏数组的空隙不返回】
▪︎find()与findIndex()
	-接收一个参数，断言函数
	-当遇到【第一个满足条件的元素时，迭代终止】，返回该元素/索引
▪︎every()和some()
	-返回值为true或false
	-every()当所有为true时才会返回true，否则为false（当遇到第一个为false时，停止遍历）
	-some()当有一个为true时返回true，全部为false时才返回false（当遇到第一个为true时，停止遍历）
▪︎reduce()和reduceRight()
	-接收两个参数
			①接收归并操作的函数 => 目前为止归并操作的累积结果，val,index,arr
			②（可选）初始值 => 会赋给函数的第一个参数  （若没传，则数组的第一个元素的值符给函数的第一个参数）
	-返回值为【归并的值】
```

### ②打平数组 — flat( )和flatMap( )

【ES2019】

- flat( ) —— 按照可指定深度递归遍历数组，将所有元素与遍历的子数组中的元素合并为一个【**新数组返回**】

  【参数：提取嵌套数组的结构深度，默认值为1】

  ```js
  let a = [1,[2,[3,[4]]]];
  a.flat();//[1,2,[3,[4]]]
  a.flat(2);//[1,2,3,[4]]
  a.flat(Infinity);//[1,2,3,4]
  ```

  - 会自动跳过稀疏数组的空元素

- flatMap( ) —— 与map( )方法类似，不过数组会被自动打平 => a.map(f).flat( )
  - 通用版的map( )，可以把输入数组中的一个元素映射为输出数组中的多个元素
  - 允许把输入元素映射为空数组

### ③添加数组 — concat( )

- 【返回一个新数组】，不会修改原数组

  - 新数组中包含调用该方法的数组元素，也包含传入的参数

  ```js
  let a = [1,2,3];
  a.concat(4,5);//[1,2,3,4,5]
  //能打平数组参数
  a.concat([4,5],[6,7]);//[1,2,3,4,5,6,7]
  ```

- ⚠️concat( )不会递归打平数组的数组

  ```js
  a.concat(4,[5,[6,[7]]]);//[1,2,3,4,5,[6,[7]]]不会打平嵌套的数组
  ```

### ④实现栈和队列操作 — push( )、pop( )、shift( )、unshift( )

- push( )
  - 在数组末尾添加一个或多个新元素
  - 返回**数组新长度**
  - 不会打平数组参数，可以使用扩展操作符...

- pop( )
  - 删除数组最后面的元素，减少数组长度
  - 返回**删除的值**

<p style="color:#cd5a4b;font-size:18px">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;⚠️push()和pop()把数组作为栈操作，都会就地修改数组</p>

```js
let stack = [];
stack.push(1,2);   //stack == [1,2],返回新数组长度2
stack.pop();       //stack == [1],返回删除的值2
stack.push([4,5]); //stack == [1,[4,5]],返回新数组长度2
stack.pop();       //stack == [1],返回删除的值[4,5]
```

- unshift( )
  - 在数组开头添加一个或多个元素
  - 返回数组新长度

- shift( )
  - 删除数组开头的第一个元素
  - 返回删除的值

<p style="color:#cd5a4b;font-size:18px">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;⚠️unshift()和shift()可以实现栈，但效率不如push()和pop()，因为在数组开头添加或删除元素时都要向上或向下移动元素</p>

<p style="color:#2a63a4;font-size:16px">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;实现队列——使用push()在末尾添加元素，使用shift()在开头删除元素</p>

```js
let q = [];
q.push(1,2); //q == [1,2]
q.shift();   //q == [2],返回1
q.push(3);   //q == [2,3]
q.shift();   //q == [3],返回2
```

<p style="color:#cd5a4b;font-size:18px">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;⚠️unshift一次插入和多次插入的数组顺序是不同的</p>

```js
let a = [];
a.unshift(1);  //a == [1]
a.unshift(2);  //a == [2,1]
a = [];
a.unshift(1,2);//a == [1,2]
```

### ⑤ 处理连续区域的方法 — slice()、splice()、fill()、copyWithin()

- slice( ) —— 【**不会修改调用它的数组**】

  - 返回一个数组的切片或子数组
  - 接收两个参数 —— 指定要返回切片的起始位置
    - 指定两个参数： **包括第一个参数**指定的元素，但**不包括第二个参**数指定的元素
    - 指定一个参数：从该参数指定的位置到数组末尾的所有元素
    - 如果参数是负值：相对于数组长度指定数组元素（例如：-1指倒数第一个元素、-2指倒数第二个元素）

  ```js
  let a = [1,2,3,4,5];
  a.slice(0,3);//[1,2,3]
  a.slice(3);//[4,5]
  a.slice(1,-1);//[2,3,4]
  a.slice(-3,-2);//[3]
  ```

- splice( ) —— 随数组进行插入和删除的通用方法 【**会修改调用它的数组**】

  - 返回被删除元素的数组，原数组会被改变
  - 参数
    - 第一个参数：插入或删除操作的**起点位置**，
    - 第二个参数（可选）：从数组中**删除的元素个数**，若省略，从起点位置元素开始的所有元素都删除
    - 后面的参数：在第一个参数指定的位置**插入到数组中的元素**

  ```js
  let a = [1,2,3,4,5,6,7,8];
  a.splice(4);//a == [1,2,3,4],返回[5,6,7,8]
  a.splice(1,2);//a == [1,4],返回[2,3]
  a.splice(1,1);//a == [1],返回[4]
  ```

  ```js
  let a = [1,2,3,4,5];
  a.splice(2,0,"a","b");//a == [1,2,"a","b",3,4,5],返回[]
  a.splice(2,2,[1,2],3);//a == [1,2,[1,2],3,3,4,5],返回["a","b"]
  ```

- fill( ) —— 将数组的元素或切片设置为指定的值【**会修改调用它的数组**】

  - 返回修改后的数组
  - 参数
    - 第一个参数：把数组元素设置成的目标值
    - 第二个参数（可选）：指定起始索引，若省略则从索引0开始填充
    - 第三个参数（可选）：指定终止索引（不包括这个索引的元素值），若省略则一直填充到数组末尾

  ​			（可以传入负值，相较于数组的末尾指定索引）

  ```js
  let a = new Array(5);//创建一个长度为5的空数组
  a.fill(0);//a == [0,0,0,0,0]
  a.fill(9,1);//a == [0,9,9,9,9]
  a.fill(8,2,-1);//a == [0,9,8,8,9]
  ```

- copyWithin( ) —— 把数组切片复制到数组中的新位置【**会修改调用它的数组，不会改变数组的长度**】

  - 返回修改后的数组
  - 参数
    - 第一个参数：指定第一个元素复制到的目的索引
    - 第二个参数（可选）：指定要复制的第一个元素的索引，若省略，默认值为0
    - 第三个参数（可选）：指定要复制的元素切片的终止索引（不包括该索引的元素），若省略，默认使用数组长度

  ​					（可以传入负值，相较于数组的末尾指定索引）

  ```js
  let a = [1,2,3,4,5];
  a.copyWithin(1);//a == [1,1,2,3,4]
  a.copyWithin(2,3,5);//a == [1,1,3,4,4]
  a.copyWithin(0,-2);//a = [4,4,3,4,4]
  ```

### ⑥ 数组索引方法

- indexOf( )与lastIndexOf( ) —— 搜索指定的值，并**返回第一个找到的元素的索引**（没找到则返回-1）

  【字符串也有这种索引方法，区别在于第二个参数为负值时会被当作0】

  -> indexOf( )         从前到后搜索数组

  -> lastIndexOf( )   从后到前搜索数组

  - 参数

    - 第一个参数：要搜索的元素值

    - 第二个参数（可选）：指定从哪个位置开始搜索，若省略，indexOf( )会从头开始搜索，lastIndexOf( )会从尾开始搜索

      （可以传入负值，相较于数组的末尾指定索引）

  ```js
  let a = [0,1,2,1,0];
  a.indexOf(1);//返回1
  a.lastIndexOf(1);//返回3
  a.indexOf(3);//返回-1
  ```

<p style="color:#2a63a4;font-size:16px">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;indexOf()第二个参数可以用来找到除第一个之外的匹配值</p>

```js
//从数组arr中找到所有值为x，返回匹配索引的数组
function findAll(arr,x) {
  let re = [],
      len = arr.length,
      start = 0;
  while(start < len) {
    start = arr.indexOf(x,start);
    if(start === -1) break;
    re.push(start);
    start += 1;
  }
  return re;
}
```

- includes( ) => 可以检测数组中的NaN值

  【ES2016】

  - 接收一个参数：查找的值 
  - 若该值存在则返回true，否则返回false

  ```js
  let a = [1,true,3,NaN];
  a.includes(true);//返回true
  a.includes(2);//返回false
  a.includes(NaN);//返回true
  a.indexOf(NaN);//返回-1,indexOf()无法找到NaN
  ```

### ⑦ 数组排序方法

- sort( ) 【**会修改调用它的数组**】

  - 返回排序后的数组
  - 参数
    - 不传参时：按字母顺序对数组元素排序（若数组包含未定义的元素时，这些未定义的元素会被排到末尾）
    - **对非字母顺序的排序** => 比较函数
      - 返回值大于0      升序
      - 返回值小于0      降序

  ```js
  let a = [33,4,111,2];
  a.sort();//按字母顺序排序,[111,2,33,4]
  a.sort((a,b) => a-b);//按数值升序，[2,4,33,111]
  a.sort((a,b) => b-a);//按数值降序，[111,33,4,2]
  ```

- reverse( ) ——反转数组元素的顺序【**会修改调用它的数组**】

  - 返回反序后的数组

  ```js
  let a = [1,3,12,5,20];
  a.reverse();//[20,5,12,3,1]
  ```

### ⑧ 数组转换为字符串

- join( ) —— 把数组的所有元素转换为字符串，然后把它们拼接起来并返回结果字符串【**不会修改调用它的数组**】

  （String.split( )的反向操作）

  - 返回结果字符串
  - 参数（可选）：字符串参数，用于分隔字符串中的元素，若不指定，默认用逗号“,”分隔

  ```js
  let a = [1,2,3];
  a.join();//返回"1,2,3"，默认用逗号分隔
  a.join(" ");//返回"1 2 3"，使用空格分隔
  a.join("");//返回"123",没有分隔
  let b = new Array(10);
  b.join("-");//返回"---------",包含9个连字符的字符串
  ```

- toString( ) —— 逻辑与没有参数的join( )方法一样

  ```js
  [1,2,3].toString();//"1,2,3"
  ["a","b","c"].toString();//"a,b,c"
  [1,[2,"c"]].toString();//"1,2,c" 
  ```

- toLocalString( ) —— toString( ) 方法的本地化版本，将每个数组元素转换为字符串，再使用**当地分隔符字符串**拼接结果字符

### ⑨ 静态数组函数

​			—— 通过Array构造函数调用，而非数组调用

- Array.of( )          【参考4.1创建数组内】

- Array.from( )     【参考4.1创建数组内】

- Array.isArray( ) —— 用于确定一个未知值是不是数组

  - 返回true或false

  ```js
  Array.isArray([]);//true
  Array.isArray({});//false 
  ```

## 7.类数组对象

#### 🌟数组区别于其他对象的特性

（并非定义数组的本质特性）

```text
▫︎ 数组的length属性会在新元素加入时自动更新
▫︎ 设置length为更小的值时会截断数组
▫︎ 数组从Array.proyotype继承有用的方法
▫︎ Array.isArray()对数组返回true
```

- 类数组：不能直接调用数组方法或期待length属性有特殊的行为，但可以用数组某些方法**遍历**

```js
//遍历类数组对象
let a = {};

//添加属性让其变为类数组对象
let i = 0;
while(i<10) {
  a[i] = i * i;
  i++;
}
a.length = i;

//像遍历一个真正的数组一样遍历对象
let total = 0;
for(let j=0; j<a.length; j++) {
  total += a[i];
}
```

- 类数组对象不会继承Array.prototype( )，因此不能直接在其上调用数组方法

  - Array.prototype.XX.call( )

    ```js
    let a = {"0": "a","1": "b","2": "c",length: 3};
    Array.prototype.join.call(a,"+");// "a+b+c"
    Array.prototype.map.call(a,x => x.toUpperCase());//["A","B","C"]
    Array.prototype.slice.call(a,0);//["a","b","c"] 真正的数组副本（把该元素复制到了真正的数组对象中）
    Array.from(a);                  //["a","b","c"] 更容易的数组复制
    ```

## 8.作为数组的字符串

- 访问字符串 

  - charAt( )
  - [ ]

- **字符串是不可修改的值**，因此将其当成数组使用时，是**只读数组**

- 能够使用泛型的字符串方法【会修改数组的方法都是不起作用的】

  如：`Array.prototype.join.call("javascript"," ");//"j a v a s c r i p t"`

# 六、函数

## 1.定义函数

### ① 函数声明语句

```text
▫︎ function关键字
▫︎ 函数命名标识符  =>  新定义的函数对象会赋值给这个变量
▫︎ 一对圆括号（中间包含逗号分隔的0或多个标识符） =>  参数（局部变量）
▫︎ 一堆花括号 {函数体}
```

- **函数的名字 → 【变量】 → 函数本身**
- 函数语句会被**提升**到包含脚本、函数或代码块的顶部（调用代码可以出现在函数定义代码之前）
- return —— 导致函数停止执行并将其表达式的值（如果有的话）返回给调用者
  - 如果return语句没有关联的表达式，则函数的返回值为undefined
  - 如果函数不包含return语句，则简单执行函数体内的每个语句，直到最后向调用者返回undefined

### ② 函数表达式

```js
//可以把函数表达式赋给一个值（变量或常量）
const square = function(x) { return x*x; };

//函数表达式也可以包含函数名字，对递归有用
const f = function fact(x) { if(x<=1) return 1; else return x*fact(x-1); };

//函数表达式也可以用作其他函数的参数
[3,2,1].sort(function(a,b) { return a-b; });

//函数表达式也可以定义完立即调用
let tensquared = (function(x) {return x*x;}(10));
```

- 函数名（可选），多数函数表达式没有名字

  - 若要引用自身，则可以带函数名

    

#### ⚠️函数声明语句与函数表达式(赋给一个变量f)有 重要区别

```text
▫︎ 函数声明语句
	◦ 先创建好函数对象，再运行包含它们的代码块
	◦ 函数的定义会被提升到顶部，可以在函数语句之前就调用
▫︎ 函数表达式
	◦ 在定义它们的表达式实际被求值之前是不存在的
	◦ 把函数表达式赋值给变量之前是无法引用的，因此不能在定义之前被调用，即不会被提升
```



### ③ 箭头函数

( ) => { }                    —— 函数表达式

- 简洁语法

  - 如果函数体只有一个return语句 => 忽略return关键字、分号及{ }

    例：`const sum = (x,y) => x+y;`

  - 如果函数只有一个参数 => 省略( )

    例：`const polynomial = x => x*x + 2*x + 3`

  - ⚠️没有参数必须要把( )写出来

    `const fun = () => 42;`

- 如果函数return的返回值是一个对象字面量，那么要加上圆括号 ( {return的返回值} ) ，避免歧义
- **this** => 从定义自己的环境中继承
- 没有prototype属性

## 2.调用函数

```text
函数代码不在定义函数时执行，而在调用函数的时候执行

五种方式调用：
▫︎ 作为函数
▫︎ 作为方法
▫︎ 作为构造函数
▫︎ 通过call()或apply()方法间接调用
▫︎ 通过JS语言特性隐式调用
```

### ① 函数调用

​                     —— 通过<u>函数调用表达式</u>是被作为函数或方法调用（若函数式对象的属性或数组元素，则是一个方法调用表达式）

- 非严格模式下的函数调用，上下文**this值为全局对象**
- 严格模式下，this为undefined

（可以区分当前是否为严格模式）

### ② 方法调用

​					 —— 方法就是函数保存为对象的属性

给o对象定义一个名为m的方法：`o.m = f;`

调用o对象里的m方法：`o.m();`

- 方法调用表达式中，**this指向o对象**
- 任何作为方法的函数实际上会隐式收到一个参数，即调用他的对象

### ③ 构造函数调用

​						—— 在函数或方法调用前加了一个关键字new

- 构造函数调用在没有参数时可以省略括号

  ```js
  o = new Object();
  o = new Object;
  ```

- 构造函数调用时会创建一个空对象，这个对象会继承构造函数的prototype属性指定的对象
- **this指向新创建出的对象**
- 构造函数正常情况不使用return关键字，隐式返回这个对象

### ④ 间接调用

​						—— JS函数是对象，也包含两个方法 call( ) 和 apply( ) => 指定调用的this值

- call( ) 
- apply( )  参数为数组

## 3.函数的实参与形参

### ① 可选形参与默认值

- 实参少于形参

  - 多出的形参会获得默认值undefined

  - 多出的形参也能够自定义**可选参数**

    - 使用 if语句 或 ||

      ```js
      function getPropertyNames(o,a) {
        //if(a === undefined) a = [];
        a = a || [];
        for(let property in o) a.push(property);
        return a;
      }
      let o = {x:1}, p = {y:2, z:3};
      let a = getPropertyNames(o);// a == ["x"]
      getPropertyNames(p,a);// a == ["x","y","z"]
      ```

    - 【ES6】在形参后直接加上等号与**形参默认值**

      ```js
      function getPropertyNames(o,a=[]){
        for(let property in o) a.push(property);
        return a;
      }
      ```

      <p style="color:#cd5a4b;font-size:18px">如果函数参数默认值是变量，那么前面的参数值可以定义后面的参数默认值</p>

      `const rectangle = (width, height=width*2) => ({width,height});`

### ② 剩余形参与可变长度实参列表

编写在调用时传入比形参多任意数量的实参函数 —— 可变参数函数、可变参数数量函数、变长函数

- 【ES6】剩余形参
  - `function fn(a,...b) { };`
  - 函数声明中的最后一个参数，多余的实参会以**数组**形式保存在剩余形参中
  - 剩余形参可以为空数组，但默认值永远不会为undefined

## 4.函数作为值

🌟函数不仅是**语法**，也是**值**

```js
function add(x,y) {return x+y;}
function substract(x,y) {return x-y;}
function multiple(x,y) {return x*y;}
function divide(x,y) {return x/y;}

//接收前面定义的任意一个函数作为参数，然后再用两个操作数调用它
function operate(operator,operand1,operand2) {
  return operator(operand1,operand2);
}
 
//计算(2+3)+(4*5)的值
let i = operate(add,operate(add,2,3),operate(multiple,4,5));
```

```js
//定义在对象字面量中
const operators = {
  add: (x,y) => x+y,
  substract: (x,y) => x-y,
  multiple: (x,y) => x*y,
  divide: (x,y) => x/y,
  pow: Math.pow
};

function operator2(operation,operand1,operand2) {
  if(typeof operators[operantion] === 'function') {
    return operators[operation](operand1,operand2);
  }	
  else throw "unknown operator"; 
}

operator2("add","hello",operate2("add"," ",world))// "hello world"
operate2("pow",10,2)//100
```

- 函数是一个**特殊的对象**，也就意味着函数可以有自己的**属性**

## 5.函数作为命名空间

​	—— 函数体内声明的变量在函数外部不可见

- 函数可以作为**临时命名空间**，可以保证其定义的变量不会污染全局命名空间

## 6.闭包

​	—— 函数对象与作用域组合起来解析函变量的机制【严格来讲，所有JS函数都是闭包】

-  JS使用**词法作用域**
- 函数执行时使用的是**定义函数时生效的变量作用域**，而不是调用函数时生效的变量作用域
- 本质：捕获自身定义所在外部函数的局部变量（及参数）绑定

<p style="color:#cd5a4b;font-size:18px">🌟 定义函数与调用函数的作用域不同时</p>

- 闭包 —— 通过一系列的方法，将函数内部的变量（局部变量）转化为全局变量【将函数内部与外部连接起来的一座桥梁】
  - 链式作用域结构：父对象的所有变量，对子对象都是可见的，反之不成立

## 7.函数属性、方法、构造函数

### ① length属性

- 只读
- 表示函数的元数 —— 函数声明的**形参个数**（调用函数时应该传入的参数个数）
  - 若函数有剩余形参，那这个剩余形参不包含在length属性内

### ② name属性

- 只读
- 定义时使用的名字
  - 未命名函数 ： 第一次创建这个函数时赋给该函数的变量名或属性名

- 记录调试或排错消息

### ③ prototype属性

除箭头函数，所有函数都有prototype属性

### ④ call( )和apply( )方法

- 间接调用一个函数
- 参数
  - 第一个参数：函数调用上下文（在函数体内会变成this关键字的值）
  - 其余参数：传给被调用的函数作为参数

- 箭头函数的this值不会被call( )和apply( )方法重写

### ⑤ bind( )方法

- 将函数绑定到对象（改变当前的this值）

  ```js
  function f(y) {return this.x + y;}
  let o = {x: 1};
  let g = f.bind(o);//将this指向o对象
  g(2);// 3
  let p = {x:10,g};
  p.g(2);//3 this仍然绑定在o上，而非p上
  ```

- 箭头函数中使用bind，绑定不起作用

- bind后面的参数也会随this一起被绑定 => 柯里化

  ```js
  let sum = (x,y) => x + y;
  let succ = sum.bind(null,1);//将第一个参数x绑定为1
  succ(2);//=> 3，先绑定到1，2会传给参数y
  
  function f(y,z) {return this.x + y + z; }
  let g = f.bind({x:1},2);//将this值绑定到对象{x:1}，将参数y绑定到2
  g(3);// => this.x绑定到1，y绑定到2,3传给参数z
  ```

### ⑥ toString( )方法

### ⑦ Function( )构造函数

- 可以接收任意多个字符串参数
  - 最后一个参数：函数体
  - 其余参数（可以没有）：函数参数名

- 创建的是**匿名函数**
- Function( )创建的函数不使用词法作用域

# 七、类

多个对象经常需要共享一些属性，此时可以为这些对象定义一个类

## 1.类和原型

​	**类** —— 一组对象从同一个**原型对象**继承属性 【**类声明不会提升、块级作用域**】

- 如果定义了一个原型对象，然后使用Object.create( )创建一个继承它的对象，那么我们就定义了一个JS类

- 一个类的实例需要进一步初始化 —— 定义一个函数创建和初始化新对象

  ```js
  function range(from,to) {
    //创建一个新对象
    let r = Object.create(range.methods);
    r.from = from;
    r.to = to;
   //返回新对象
    return r;
  }
  
  range.methods = {
    includes(x) {
      return this.from <= x && x <= this.to;
    }
  }
  
  let r = range(1,3);//创建一个范围对象
  r.includes(2);//true
  ```

## 2. 类和构造函数

构造函数constructor —— 专门用于创建和初始化由类创建的对象

构造函数的**prototype属性**将被用作新对象的**原型**

- 命名以大写字母开头

- 以new关键字生成实例对象后，自动调用该方法

  - 使用new<u>实例化Person</u>就相当于使用new<u>调用其构造函数</u>

- 一个类只能拥有一个名为constructor的构造函数；如果没有则会自动创建一个空的constructor

- 原型对象的命名方式：Fun.prototype —— 作为新Fun对象的原型

  ```js
  function Range(from,to) {
    //不创建也不返回对象，只初始化this
    this.from = from;
    this.to = to;
  }
  
  Range.prototype = {
    includes: function(x) {return this.from <= x && x <= this.to;}
  };
  
  let r = new Range(1,3);//创建一个Range对象
  r.includes(2);//true
  ```

<p style="color:#cd5a4b;font-size:18px">🌟 使用new调用构造函数会执行如下操作</p>

```text
1.在内存中创建一个新对象
2.这个新对象内部的[[prototype]]指针被赋值为构造函数的prototype属性
3.构造函数内部的this被赋值为这个新对象（即this指向新对象）
4.执行构造函数内部的代码 —— 给新对象添加属性
5.如果构造函数返回非空对象，则返回该对象；否则，返回刚创建的新对象
```

### 构造函数、类标识、instanceof

- 类标识 —— 原型对象
  - 当且仅当两个对象继承同一个原型对象时，他们才是同一个类的实例

- 类的外在表现 —— 构造函数（类的公共标识）
  - 构造函数名字通常用作类名

- instanceof  —— f instanceof Fun 
  - 检测f是否继承Fun.protoptype
  - 不一定是直接继承

## 3.使用Class关键字的类

【ES6】即基础的类定义机制的“语法糖“

```text
▫︎ Class关键字声明
▫︎ 使用对象字面量方法简写形式，方法之间没有逗号
▫︎ 关键字constructor用于定义类的构造函数
  - 若类不需要任何初始化，可以省略constructor，解释器会隐式创建一个空构造函数
```

```js
class Range {
  constructor(from,to) {
    this.from = from;
    this.to = to;
  }
  includes(x) {return this.from <= x && x <= this.to;}
}

let r = new Range(1,3);//创建一个Range对象
r.includes(2);//true
```

- extends —— 定义一个继承另一个类的类

  ```js
  class Span extends Range {
    constructor(start,length) {
      if(length >= 0) {
        super(start,start + length);
      } else {
        super(start + length,start);
      }
    }
  };
  ```

- class声明体中的所有代码默认处于**严格模式**
- **类声明不会提升** —— 不能在声明类之前初始化它

## 4.类的实例、原型以及类的成员

### getter与setter

- 在class内部使用get与set关键字，对某个属性设置存值函数和取值函数，拦截该属性的存取行为

```js
class Person {
  constructor(test) {
    this.test = test || '默认值';
  }
  get prop() {
    return this.test;
  }
  set prop(value) {
    console.log(`setter prop value:${value}`);
    this.test = value;
  }
}
const p = new Person('1');
p.prop;//1
p.prop = '2';//setter prop value: 2
p.prop;//2
```

### Generator方法 （方法前加*）

```js
class Person {
  constructor(...args) {
    this.args = args;
  }
  * generatorFun() {
    for(let arg of this.args) {
      yield arg;
    }
  }
}
const a = new Person(1,2,3,4);
const generatorNext = a.generatorFun().next; 
generatorNext();//{value:1,done:false}
generatorNext();//{value:2,done:false}
generatorNext();//{value:3,done:false}
generatorNext();//{value:4,done:false}
generatorNext();//{value:undefined,done:true}
```

### this指向

- 默认指向类的实例

- 当找不到this，指向该方法运行时所在的环境，但class内部是严格模式，this实际指向undefined

  - 解决方法① : 构造方法中绑定this

    ```js
    class Person{
      constructor() {
        this.text = '1';
        this.getText = this.getText.bind(this);
      }
      getText() {
        console.log(this.text);
      }
    }
    ```

  - 解决方法② : 使用箭头函数

    ```js
    class Person{
      constructor() {
        this.text = '1';
      }
      getText = () => {
        console.log(this.text);
      }
    }
    ```

  - 解决方法③ : 使用proxy在获取方法是自动绑定this

## 5.静态方法、静态属性、静态代码块

使用static定义的属性，只能class自己用，不能通过实例继承

- 静态方法（当前类自身属性）

  —— this指向当前类，而不是实例对象

- 静态代码块   static { }

  —— 在class内部创建块状作用域，可以通过this访问class所有成员变量，包括#私有变量

  - 按顺序执行，父类优先执行，一个类中允许多个静态代码块的出现
  - 私有变量外部是访问不了的，但是可以通过静态代码块，就能将私有属性暴露给外部变量

## 6.私有属性、私有方法

—— # 只能在类的内部访问的属性和方法，外部不能访问，不可以直接通过class实例引用

- 私有属性 —— 只能内部读取或写入
- 私有方法 —— 只能内部调用，外部调用会出错

## 7.为已有类添加方法

基于原型的继承机制是**动态**的 —— 创建对象之后修改原型的属性，对象会继承修改后的属性

## 8.子类

子类构造函数通常必须调用父类构造函数才能将实例完全初始化

### ① 子类与原型

父类A( )与子类B( ) —— 子类B( )的实例也是父类A( )的实例

- 通过B( )构造函数创建的对象会继承B.prototype属性

- 创建该对象时让他继承A.prototype

### ② 通过extends和super创建子类

【ES6】

- 子类 **extends** 父类

  - 子类实例不仅会继承父类的实例方法，子类本身也继承了父类的静态方法

  -  类的静态方法和属性是可以继承的，私有属性和方法是不能继承的

     		—— 可以从继承的公有方法和静态方法中获取其私有属性或调用其私有方法

- 在构造函数中使用**super( )**

  - 子类可以通过super关键字调用**父类构造函数**或**父类中被覆盖的方法**

  - 只能在继承类的constructor构造函数、实例方法、静态方法中使用

  - 在constructor中super( )在顶部首段执行代码

    ```text
    ① super只能在继承类的构造函数、静态方法中使用
    ② 不能单独引用super关键字 —— 要么用它调用构造函数、要么引用静态方法
    ③ 调用super会调用父类构造函数，并将返回的实例赋值给this
    ④ super()的行为如同调用构造函数，如果需要给父类构造函数传参，则需要手动传入
    ⑤ 如果没有定义类构造函数，在实例化继承时会调用super()，而且会传入所有传给继承类的参数
    ⑥ 在类构造函数中，不能在调用super()之前引用this
    ⑦ 如果在继承类中显示定义了构造函数 —— 调用super()、返回一个对象
    ```

<p style="color:#cd5a4b;font-size:18px">⚠️ 注意点</p>

```text
▫︎ 如果使用extends关键字定义了一个类，那么这个类的构造函数必须使用super()调用父类构造函数
▫︎ 如果没有在子类中定义构造函数，解释器会自动创建一个
▫︎ 通过super()调用父构造函数之前，不能在构造函数中使用this关键字【确保父类先于子类得到初始化】
▫︎ super关键字很像this关键字，它引用当前对象，但允许访问父类定义的被覆盖的方法
```

# 八、模块

【ES6】使用import和export关键字定义自己的模块，js模块化依赖代码打包工具

## 1.基于类、对象、闭包的模块

- 类 —— 充当自己方法的模块
  - 类的方法之所以能相互独立，因为每个类的方法都被定义为独立原型对象的属性

- 对象 —— 模块 （给对象添加属性不影响全局命名空间，也不影响其他对象的属性）

## 2.Node中的模块

编写Node程序时，可以随意将程序拆分到任意多个文件中

### ① Node的导出

全局**exports对象**

- exports.XX 

  ```js
  exports.mean = data => data.reduce(sum)/data.length;
  ```

- module.exports = XX

  ```js
  module.exports = class BitSet extends AbstractWritableSet { }
  ```

- 在模块末尾导出一个对象 module.exports = { XX, XX }

  ```js
  const mean = data => data.reduce(sum)/data.length;
  const stddev = d => {
    let m = mean(d);
    return Math.sqrt(d.map(x => x - m).map(square).reduce(sum)/(d.length-1));
  }
  module.exports = { mean, stddev };
  ```

 ### ② Node的导入

- 调用require( )函数导入其他模块
  - 参数 —— 要导入模块的名字
  - 返回值 —— 该模块导出的值

- 导入

  - 导入**内置的系统模块**或**通过包管理器安装在系统上的模块** —— 可以使用模块的非限定名

    ```js
    //Node内置模块
    const fs = require("fs");
    const http = require("http");
    
    //第三方模块
    const express = require("express");
    ```

  - 导入**自己代码中的模块**

    - 模块名 —— 通常使用相对路径（ ./ 或 ../ 开头），表示相对于当前的目录或父目录

      ```js
      //可以省略.js后缀
      const states = require('./states.js');
      ```

- 

  - 模块只**导出一个函数或类** —— 调用require( )取得返回值

  - 模块**导出一个带多个属性的对象**

    - ① 导入整个对象

    - ② 解构赋值，只导入打算使用的特定属性

      ```js
      const { stddev } = require('./states.js');
      ```

## 3.ES6中的模块

ES6为JS添加了import和export关键字

### ① ES6的导出

- 导出常量、变量、函数、类，在声明前加上export关键字即可

  ```js
  //常量
  export const PI = Math.PI;
  //函数
  export function fun(d) {return d * PI / 180};
  //类
  export class Circle {
    constructor(r) {this.r = r};
    area() {return PI * this.r * this.r}
  }
  ```

- 取代多个export关键字：在模块末尾使用一个export语句 

  ```js
  export {Circle, fun, PI}//不会定义对象字面量（简化语法）
  ```

- 一个模块只**导出一个值**（函数或类） => export default

  ```js
  export default class BitSet { } //export default后面的花括号是会被导出的对象字面量
  ```

- export关键字只能出现在**代码顶层**，不能再类、函数、循环、条件内部导出值

### ② ES6的导入

- import关键字只能出现在**代码顶层**，不能再类、函数、循环、条件内部导出值

- 一个模块所需的导入应该放在模块的开头 —— **模块的导入会被“提升”到顶部**

- 模块标识符字符串必须是一个以 **/** 开头的绝对路径，或是以 **./** 或 **../** 开头的相对路径

- 导入

  - import**导入默认导出的模块**（导入一个）

    ```js
    import BitSet from './bitset.js';
    ```

  - 导入多个值 —— 使用{ }，会被提升到模块顶部

    ```js
    import { mean, stddev } from './states.js';
    ```

- 

  - 默认导出的模块导出时不需要名字，在导入这些值时可以再提供一个局部名

  - 非默认导出的模块导出时又名字，在导入这些值时可以通过名字引用

  - 导入**没有任何导出的模块 ** —— 会在被首次导入时运行一次（时候导入时则什么也不做）

    ```js
    import './analytics.js';
    ```

### ③ 导入和导出时重命名

as关键字

- 导入

```js
import {render as renderImage} from './imageutils.js';
import {render as renderUI} from './ui.js';
```

- 导入默认导出的没有名字的模块（用default充当一个占位符）

  ```js
  import { default as Histogram, mean, stddev } from './histogram-stats.js';
  ```

- 导出

  - as前是一个**标识符**，而非表达式

    ```js
    export {Math.sin as sin};//SyntaxError
    ```

### ④ 再导出

导入真正要用的函数，而不会因导入不需要的代码造成体积膨胀

```js
export { mean } from './stats/mean.js';
export {stddev } from './stats/stddev.js';
```

- 导出一个模块中的所有命名值

  ```js
  export * from './stats/mean.js';
  ```

- 可以用as重命名

# 九、JavaScript标准库（API）

## 1.集合与映射

### ①Set类（集合）

- 集合 —— 一组值（与数组类似）
  - 没有索引或顺序
  - 不允许重复

- 创建集合对象 —— new Set( )

  - 可选参数：可迭代对象

  ```js
  let s = new Set();//一个新、空集合
  let t = new Set([1,s]);//一个有两个成员的新集合
  let unique = new Set("Mississippi");//4个元素："M""i""s""p"
  ```

- size属性（相当于数组的length）

- 集合不一定在创建时初始化，可以在创建后通过**add( )**、**delete( )**、**clear( )**方法给他添加元素或从中删除元素

  ```js
  let s = new Set();  //创建一个空集合
  s.size;             // => 0
  s.add(1);              //添加一个数值
  s.size;             // => 1 现在集合有了一个成员
  s.add(1);
  s.size;             // => 1 集合不存在重复的值
  s.add(true);
  s.size;             // => 2
  s.add([1,2,3]);     //添加了一个数组值
  s.size;             // => 3 添加的一个数组，而不是数组的元素
  s.delete(1);        // true 成功删除元素1
  s.size;             // => 大小变为2
  s.delete("test");   // false "test"不是成员，删除失败
  s.delete(true);     // true 
  s.delete([1,2,3]);  // false 集合中包含的是另一个数组
  s.size;             // => 1 集合中还有一个数组
  s.clear();          //清空集合
  s.size;             // => 0
  ```

  - add( ) —— 接收一个参数（若为数组，则会把数组而不是数组元素添加到集合中）
    - 返回**调用它的集合**
    - 给集合添加多个值，可以连缀调用 —— 例：s.add('a').add('b').add('c')

  - delete( ) —— 一次只删除一个集合元素
    - 返回**布尔值**

  - <p style="color:#cd5a4b;font-size:18px">🌟 集合成员是根据   严格相等（全等）判断是否重复</p>

  - has( ) —— 检查某个值是不是集合成员

    ```js
    let s = new Set([2,3,5,7]);
    s.has(2);  // => true：2是一位数字的素数
    s.has(3);  // => true：3也是
    s.has(4);  // => false：4不是
    s.has("5");// => false："5"是一个字符串，不是数值
    ```

- set类是**可迭代的** 

  -  for of 

    ```js
    let sum = 0;
    for(let p of s) {
      sum += p;
    }
    sum // => 17：2+3+5+7
    ```

  - 扩展运算符... 

    把集合转换为真正的数组或参数

    ```js
    [...s];// => [2,3,5,7] 
    Math.max(...s);// => 7
    ```

- set集合是  **无索引的**  ，并不是无序的（会记住元素插入的顺序）

- set也可以用forEach( )方法（集合没有索引，所以回调函数的第一和第二个参数都是元素的值）

### ② Map类（映射）

- Map对象表示 **一组被称为键的值，每个值都关联着（映射到）另一个值**
  - 类似于数组，但并不局限于用连续整数作为键，允许用任何值作为“索引”

- 创建Map对象 —— new Map( )

  - 可选参数：可迭代对象

    ``let m = new Map();//创建一个空、新映射``

  - 产出值：包含两个元素的数组 [ key, value ]

    —— 若想在创建映射时初始化

    -  通常要把关联的键和值写成数组的数组的形式

      ```js
      let n = new Map([
        ["one",1],
        ["two",2]
      ]);               //初始化新映射，包含字符串到数值的映射
      ```

    - 使用Map( )构造函数复制其他映射 

      ```js
      let copy = new Set(n);//一个新映射，与映射n拥有相同的键和值
      ```

    -  从已有对象复制属性名和值

      ```js
      let o = { x: 1, y:2 };//一个有两个属性的对象
      let p = new Map(Object.entries(o));//相当于new Map([["x",1],["y",2]])
      ```

- size属性 —— 保存映射中有多少个键

- 方法

  - get( ) —— 查询键关联的值

  - set( ) —— 添加新的 键/值 对

    - 若set( )传入一个映射中已存在的键，则会修改与该键关联的值，而不是添加新的 键/值 映射

    - 可以**连缀调用**

      `let m = new Map().set("one",1).set("two",2).set("three",3);`

  - has( ) —— 检查映射中是否包含指定的键
  - delete( ) —— 从映射中删除指定键及其关联值
  - clear( ) —— 删除映射中所有 键/值 对的clear( )

  ```js
  let m = new Map();   //创建一个空映射
  m.size();            // => 0
  m.set("one",1);      //映射键"one"和值1
  m.set("two",2);      //添加键"two"和值2
  m.size;              // => 2 现在映射有两个键
  m.get("two");        // => 2 返回与键"two"关联的值
  m.get("three");      // => undefined：这个键不存在
  m.set("one",true);   //修改已有键"one"对应的值
  m.size;              // => 2
  m.has("one");        // true：映射中有键"one"
  m.has(true);         // false：映射中没有键true
  m.delete("one");     // true：键"one"存在且删除成功
  m.size;              // => 1
  m.delete("three");   // false：删除不存在的键失败
  m.clear();           //删除映射中所有的键和值
  ```

  - <p style="color:#cd5a4b;font-size:18px">🌟 映射是按照   严格相等（全等）比较键</p>

    - 注意数组、对象等作为键时的情况

- 映射对象是**可迭代的**

  —— 迭代的每个值是一个包含两个元素的数组：[ 键，值 ]

  - for / of

    ```js
    for(let [key,value] of m) {
      //第一次迭代，键是"x"值是1
      //第二次迭代，键是"y"值是2
    }
    ```

  - 扩展运算符...

    ```js
    let m = new Map([["x",1],["y",2]]);
    [...m] // => [["x",1],["y",2]]
    ```

    - keys( ) —— 返回可迭代对象用于按插入顺序迭代的键

    - values( ) —— 返回可迭代对象用于按插入顺序迭代的值

    - entries( ) —— 返回可迭代对象用于按插入顺序迭代的 键 / 值 对（与直接映射一样）

      ```js
      [...m.keys()] // => ["x","y"]：只有键
      [...m.values()] // => [1,2]：只有值
      [...m.entries()] // => [["x",1],["y",2]]：等价于[...m]
      ```

- 会记住映射插入的顺序，并不是无序的
- 映射也可实现forEach方法 —— 注意回调函数的第一个参数为值value，第二个参数为键key

## 2.定型数组与二进制数据

定型数组 —— 严格来讲并不是数组（Array.isArray( )方法返回false），但能够实现所有的数组方法，外加几个自己的方法。

<p style="color:#cd5a4b;font-size:18px">🌟 定型数组与数组的区别</p>

```text
▫︎ 定型数组元素全部为 数值 ，允许指定数值的类型和大小
▫︎ 创建定型数组时必须指定长度，且长度不能再改变
▫︎ 定型数组元素在创建时始终会被初始化为0
```

- 定型数组的类型

  - JS并未定义TypedArray类，而是定义了**11种定型数组**，每种都有自己的**元素类型和构造函数**

  - 每种定型数组构造函数都有 BYTES_PER_ELEMENT属性

    ```text
    构造函数                 数据类型
    Int8Array()            有符号字节
    Uint8Array()           无符号字节
    Uint8ClampedArray()    无符号字节（上溢不归零）
    Int16Array()           有符号16位短整数
    Uint16Array()          无符号16位短整数
    Int32Array()           有符号32位短整数
    Uint32Array()          无符号32位短整数
    BigInt64Array()        有符号64位BigInt值【ES2020】
    BigUint64Array()       无符号64位BigInt值【ES2020】
    Float32Array()         32位浮点值（精度较低，范围较小，只占用一般内存）
    Float64Array()         64位浮点值：常规JavaScript数值
    ```

- 定型数组 —— length是只读的，长度不能修改

## 3.正则表达式与匹配模式

正则表达式是一种**描述文本模式的对象** —— RegExp类

### ① 定义正则表达式

- 创建方式

  - 使用RegExp构造函数

    ```js
    let pattern = new RegExp("s$"); 
    ```

  - 使用一对斜杠(/)    //

    ```js
    let pattern = /s$/; // 匹配任意以s结尾的字符串
    ```

- 正则表达式中使用的各种字符与元字符

  #### 1》字面量字符

  - 字母字符和数字 —— 匹配自身的字面值
  - 以反斜杠（/）开头的转义序列也支持一些非字母字符
    - 一些英文标点符号有特殊含义，因此可以给所有的标点字符前都加上反斜杠
    - 若要匹配\，则需要在反斜杠前加上反斜杠
    - 但部分字母和数字加上反斜杠会有特殊含义，若要匹配字面值的字母和数字都不应该加反斜杠

  #### 2》字符类

  —— 把个别字面值字符放到方括号中可以组成字符类     [ ] 

  - ^ 排除性字符类

  - a-z 表示一个字符范围

    ```js
    /[abc]/     //匹配a、b、c中任意一个字母
    /[^abc]/    //匹配除a、b、c外的任意一个字符
    /[a-z]/     //匹配a-z中的任意一个字母
    ```

#### 正则表达式字面量字符

```text
字符                       匹配目标
\0                        NUL字符
\t                        制表符
\n                        换行符
\v                        垂直制表符
\f                        进纸符
\r                        回车符
```

#### 正则表达式字符类

```text
字符               匹配目标
[...]            方括号中的任意一个字符
[^...]           不在方括号中的任意一个字符
.                表示除\n（换行）或\r（行终止符）之外的任意字符
\w               任意ASCII单词字符。=> [a-zA-Z0-9]
\W               任意非ASCII单词字符。=> [^a-zA-Z0-9]
\s               任意Unicode空白字符
\S               任意非Unicode空白字符
\d               任意ASCII数字字符。 => [0-9]
\D               任意非ASCII数字字符。 => [^0-9]
```

#### 正则表达式重复字符

```text
字符               匹配目标
{n,m}            匹配前项至少n次，但不超过m次
[^...]           不在方括号中的任意一个字符
\w               任意ASCII单词字符。=> [a-zA-Z0-9]
\W               任意非ASCII单词字符。=> [^a-zA-Z0-9]
\s               任意Unicode空白字符
\S               任意非Unicode空白字符
\d               任意ASCII数字字符。 => [0-9]
\D               任意非ASCII数字字符。 => [^0-9]
```

#### 正则表达式任选、分组和引用字符

```text
字符               含义
\|               任选：可以匹配左侧的子表达式，也可以匹配右侧的子表达式
(...)            分组：将模式分组为一个单元，以便使用*、+、?、|等。同时记住与分组匹配的字符，以便在后面的引用中使用
(?:...)          仅分组：将模式分组为一个单元，但不记住分组匹配的字符
\n               匹配与第n个分组匹配的相同字符。分组是圆括号（可能嵌套）中的子表达式，分组编号是按照左圆括号从左到右计数的。
                 由(?:开头的分组不计数
```

#### 正则表达式锚点字符

```text
字符               含义
^               匹配字符串开头。或者在使用m标志时，匹配一行的开头
$               匹配字符串末尾。或者在使用m标志时，匹配一行的末尾
\b              匹配单词边界。换句话说，匹配\w字符和\W字符之间或\w与字符串开头或末尾之间的位置（[\b]匹配退格字符）
\B              匹配非单词边界的位置
(?=p)           肯定式向前查找断言。要求后面的字符匹配模式p，但匹配结果不包含与之匹配的字符
(?!p)           否定式向前查找断言。要求后面的字符不匹配模式p
```
