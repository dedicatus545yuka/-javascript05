# -javascript05
特殊函数，对象
### 特殊函数  
#### 匿名函数  
>JavaScript 可以将函数作为数据使用。作为函数本体，它像普通的数据一样，不一定要有名字。默认名字的函数被称之为匿名函数。
```js
// 函数的定义
function(){
    console.log('this is function');
}
// 函数的调用 - 根据函数名查找定义，执行对应的函数体,但是这里函数未被定义，所以报错
fn();
```
匿名函数    
* JavaScript的语法结构并不支持匿名函数的定义
* 匿名函数本身失去了函数的含义
* 用法
    * 自调函数
    * 回调函数
#### 自调函数  
>所谓自调函数就是在定义函数后自行调用。

- 语法结构
```js
(function (a){
    console.log(a)；
})(100)；
```
* 第一个小括号：定义函数
* 第二个小括号：调用函数
* 特点 - 只能被调用一次
* 应用 - 优化全局命名空间
>其他的不同的定义方式
```js
(function(a){
    console.log(a);
}(100));
```
```js
+function(a){
    console.log(a);
}(100);
```
```js
!function(a){
    console.log(a);
}(100);
```
#### 回调函数 
>当一个函数作为参数传递给另一个函数时，作为参数的函数被称之为回调函数。
```js
var one = function(){
    return 1;
}
var two = function(){
    return 2;
}
function fn(a,b){
    return a() + b();
}
var result = fn(one,two);
console.log(result);
```
![示意图](http://a1.qpic.cn/psb?/V118JuTr0BKcy7/d6Q*nyfWgQXWb2yNGc748tZCKfBWezFBPUaCJcrDZWI!/b/dPMAAAAAAAAA&bo=GwWAAgAAAAADB74!&rf=viewer_4)      
**回调函数的一些优点**
- 它可以在不做命名的情况下传递函数（这意味着可以节省全局变量）。
- 可以将一个函数调用操作委托给另一个函数（这意味着可以节省一些代码编写工作）。
- 回调函数也有助于提升性能。
```js
// 定义函数fn() -> 由A负责 -> 使用说明文档
function fn( a, b ){
    var x = 1,y = 2;// 局部变量
    return a(x) + b(y);
}
// 调用函数fn() -> 由B负责
var result = fn( function( c ){
        console.log(c);
        return c;
    }, function( d ){
        console.log(d);
        return d;
    } );
console.log(result);
```
![示意图](http://a4.qpic.cn/psb?/V118JuTr0BKcy7/SyhimDZZscKp.zHFe53X4LjW5LZ3Cv1Uaaw1qmQMrN8!/m/dPMAAAAAAAAA&bo=GwWAAgAAAAADB74!&rf=photolist)
#### 作为值的函数  
>将一个函数作为另一个函数的结果进行返回，作为结果返回的函数称之为作为值的函数. - 实际上，是内部函数的一种特殊用法
- 在全局作用域可以得到两个函数，实际上只定义了一个函数
- 在全局作用域中调用内部函数
```js
function fn( f, args ){
    return f( args );
}
function add( num ){// 作为值的函数
    return num + 10;
}
var result = fn( add, 10 );
console.log( result );// 20
```
![示意图](http://a3.qpic.cn/psb?/V118JuTr0BKcy7/2Jpu7INjWGI8R3ZLNB6m2mHcWR.7j0qM7DG4NMyxNRI!/m/dPIAAAAAAAAA&bo=rwOAAgAAAAADBww!&rf=photolist)
### 对象
- JavaScript 中的对象，和其它编程语言中的对象一样，可以比照现实生活中的对象来理解它。  
- JavaScript 中对象的概念可以比照着现实生活中实实在在的物体来理解。 
    - 在 JavaScript 中，一个对象可以是一个单独的拥有属性和类型的实体。拿它和一个杯子做下类比，一个杯子是一个对象，拥有属性。杯子有颜色、图案、重量等等。同样，JavaScript 对象也有`属性`来定义它的特征。
- 一个 JavaScript 对象有很多`属性`。一个对象的属性可以被解释成一个附加到对象上的变量。对象的属性和普通的 JavaScript 变量基本没什么区别，仅仅是属性属于某个对象。 
- `方法`是关联到某个对象的函数，或者简单地说，一个方法是一个值为某个函数的对象属性。定义方法就象定义普通的函数，除了它们必须被赋给对象的某个属性。
#### 对象的分类
- 内置对象/原生对象  
    - 就是 JavaScript 语言预定义的对象。在 ECMAScript 标准定义，由 JavaScript 解释器/引擎提供具体实现。
- 宿主对象
    - 指的是 JavaScript 运行环境提供的对象。一般是由浏览器厂商提供实现（目前也有独立的 JavaScript 解释器/引擎提供实现），主要分为 BOM 和 DOM。
- 自定义对象
    - 就是由开发人员自主创建的对象。  
#### 创建对象  
1. **对象的初始化器方式定义** 
>使用对象初始化器也被称作通过字面值创建对象。 
```js
var obj1 = {
    // 定义对象的属性
    name : 'love',
    // 定义对象的方法
    sayMe : function(){
        console.log('this is love');
    }
}
```
2. **构造函数(Object)方式定义**  
- 通过 JavaScript 提供的预定义类型的构造函数来创建对象，如下示例:
```js
var str = new String();// 创建String类型的对象
var num = new Number();// 创建Number类型的对象
```
- 通过 JavaScript 提供的 Object 类型的构造函数来创建自定义对象，如下示例:
```js
var obj2 = new Object();
// 定义对象的属性
obj2.name = 'love';
// 定义对象的方法
obj2.sayMe = function(){
    console.log('this is love');
}
```
3. **利用 Object.create() 方法创建对象**  
```js
var obj3 = Object.create(null);// 创建一个原型为 null 的空对象。
// 定义对象的属性
obj3.name = 'love';
// 定义对象的方法
obj3.sayMe = function(){
    console.log('this is love');
}
// 对象obj4具有与对象obj3相同的属性和方法(相当于复制)
var obj4 = Object.create(obj3);
console.log(obj4.name);// love
```
#### 调用对象
>在调用之前要先定义对象的属性或方法
```js
// 创建对象
var obj = {
    // 定义对象的属性
    name : 'yuka',
    'content-type' : 'text/javascript',
    // 定义对象的方法
    sayMe : function(){
        console.log('this is love');
    }
}
// 1. 可以通过点符号来访问一个对象的属性。
    // 调用对象的属性
    console.log(obj.name);// yuka
    console.log(obj.content-type);// text/javascript,这里的属性名要去掉单引号
    // 调用对象的方法
    obj.sayMe();
// 2. JavaScript 对象的属性（方法）也可以通过方括号访问。对象有时也被叫作关联数组, 因为每个属性都有一个用于访问它的字符串值。
    // 调用对象的属性
    console.log(obj['name']);
    // 调用对象的方法
    obj['sayMe']();
    console.log(obj['content-type']);// 这里用了方括号所以要加单引号
```
![示意图](http://a1.qpic.cn/psb?/V118JuTr0BKcy7/8OWOI3ILqVBzbekQmDweb6ZJCxR6*rXT8hOq9cdW*RE!/b/dGsBAAAAAAAA&bo=GwWAAgAAAAADB74!&rf=viewer_4)
#### 遍历对象   
>JavaScript 提供了三种原生方法用于遍历或枚举对象的属性或者方法.
```js
var girl = {
    // 属性
    name : 'yuka',
    age  : 29,
    job  : 'singer',
    // 方法
    lover: function(){
        console.log('i love you');
    }
}
//1. for…in 循环: 该方法依次访问一个对象及其原型链中所有可枚举的属性和方法。
for (var propertyName in girl){
    if (girl[propertyName] instanceof Function){// 区分当前是属性还是方法
        girl[propertyName]();// 得到对象的属性或方法名 - console.log(propertyName);
    }else{
        console.log(girl[propertyName]);// 知道对象名和属性或方法名 -> 输出属性值或调用方法
    }
}
/*
2. Object.keys(obj)方法
    * 作用 - 用于遍历对象的属性或方法
    * 参数 - 遍历的对象
    * 返回值 - 得到遍历对象的所有属性或方法名，是数组类型
 */
var result = Object.keys(girl);
console.log(result);// [ 'name', 'age', 'job', 'lover' ]

// 通过循环和条件来找到对应的属性或方法
for(var i=0;i<result.length;i++){
    console.log(result[i]);// 输出属性名
    if (girl[result[i]] instanceof Function){
        girl[result[i]]();// 输出方法的值
    }else{
        console.log(girl[result[i]]);// 输出属性的值
    }
}
/*
3. Object.getOwnPropertyNames(obj)方法
    * 作用 - 用于遍历对象的属性或方法
    * 参数 - 遍历的对象
    * 返回值 - 得到遍历对象的所有属性或方法名，是数组类型
 */
var result2 = Object.getOwnPropertyNames(girl);
console.log(result2);// [ 'name', 'age', 'job', 'lover' ]
```
#### for语句的相关比较
```js
// 定义数组
var arr = [1,2,3,4,5,6,7,8,9];
// for语句 - 允许自定义循环的开始和结束位置的
for (var i=0;i<arr.length;i++){
    console.log(arr[i]);
}
// for..in语句 - 只能从开始到结束，不能自定义
for (var i in arr){
    console.log(arr[i]);
}
// for..of语句 - ES6版本新增，直接得到值，而不是序号(索引值)
for (var i of arr){
    console.log(i);
}
```
#### 访问属性出错 
```js
var girl = {
    name : 'yuka',
    lover : function(){
        console.log('i love you');
    }
}
console.log(girl.name);// 访问对象的属性是一定存在的
console.log(girl.job);// 访问对象中不存在的属性 -> undefined
girl.loves();// 报错：girl.loves is not a function
```
#### 检测对象的属性或方法 
`可以使用如下四种方法检测对象中是否存在指定属性（方法）:`
>在检测方法时不要在属性名后面加()
```js
var girl = {
    name : 'yuka',
    lover : function(){
        console.log('i love you');
    }
}
// 1.使用 undefined 进行判断。
console.log(girl.name === undefined);// 由于属性是存在的所以这里是 false
// 2.使用in关键字.
console.log('name' in girl);
// 3.Object 提供了 hasOwnProperty() 方法 - Object 是所有对象的父级，Object的属性和方法所有对象都可以直接使用
console.log(girl.hasOwnProperty('name'));
// 4.使用 if 语句进行判断。
if (girl.name !== undefined){
    // 说明对象的属性是存在的
}
if ('name' in girl) {
    // 说明对象的属性是存在的
}
if (girl.hasOwnProperty('name')) {
    // 说明对象的属性是存在的
}
// console.log(girl.hasOwnProperty('name') ? '存在':'不存在');
```
#### 操作对象的属性或者方法（增删改查）  
```js
// 创建一个对象
var girl = {
    name:'yuka',
    lover: function(){
        console.log('i love you');
    }
}
girl.age = 29;// 直接添加一个新的属性并且初始化它的值
console.log(girl.age);// 29
girl.loves = function(){ console.log('dove');}// 直接添加一个新的方法并且初始化它的值

girl['age'] = 16;// 直接改变属性的值来覆盖原来的值以达到修改的目的
girl.['loves'] = function(){ console.log('sorry');}// 同样直接改变方法的值来覆盖原来的值以达到修改的目的

//可以用 delete 操作符删除对象的属性或方法  
//  *这个属性或方法不是继承而来的
//  *删除对象的方法时，不需要小括号“()”。如果有小括号则删除失败 - delete失效
delete girl.age;
console.log(girl.age);// undefined
delete girl.loves;
girl.loves();
```
