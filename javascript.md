##  快速入门
### 数据类型
#### number
123; // 整数123
0.456; // 浮点数0.456
1.2345e3; // 科学计数法表示1.2345x1000，等同于1234.5
-99; // 负数
NaN; // NaN表示Not a Number，当无法计算结果时用NaN表示  eg:0/0
Infinity; // Infinity表示无限大，当数值超过了JavaScript的Number所能表示的最大值时，就表示为Infinity  eg:2/0
#### bool
true; // 这是一个true值
false; // 这是一个false值
2 > 1; // 这是一个true值
2 >= 3; // 这是一个false值
NaN === NaN; // false
isNaN(NaN); // true
要特别注意相等运算符==。JavaScript在设计时，有两种比较运算符：

第一种是==比较，它会自动转换数据类型再比较，很多时候，会得到非常诡异的结果；

第二种是===比较，它不会自动转换数据类型，如果数据类型不一致，返回false，如果一致，再比较。

#### null和undefined
null表示一个“空”的值，它和0以及空字符串''不同，0是一个数值，''表示长度为0的字符串，而null表示“空”。
var arr = [1, 2, 3.14, 'Hello', null, true];
arr[6]; // 索引超出了范围，返回undefined
#### 对象
```javascript
var person = {
    name: 'Bob',
    age: 20,
    tags: ['js', 'web', 'mobile'],
    city: 'Beijing',
    hasCar: true,
    zipcode: null
};
person.name; // 'Bob'
person.zipcode; // null
```
#### 变量
```javascript
var a = 123; // a的值是整数123
a = 'ABC'; // a变为字符串
```
在strict模式下运行的JavaScript代码，强制通过var申明变量，未使用var申明变量就使用的，将导致运行错误。
启用strict模式的方法是在JavaScript代码的第一行写上：
```javascript
'use strict';
```
####  string
```javascript
console.log(`多行
字符串
测试`);//多行字符串


var name = '小明';
var age = 20;
var message = `你好, ${name}, 你今年${age}岁了!`;
alert(message);

var s = 'Test';
s[0] = 'X';
alert(s); // s仍然为'Test' 字符串不可变
```
toUpperCase()把一个字符串全部变为大写：
toLowerCase()把一个字符串全部变为小写：
indexOf()会搜索指定字符串出现的位置：
```javascript
var s = 'hello, world';
s.indexOf('world'); // 返回7
s.indexOf('World'); // 没有找到指定的子串，返回-1
```
substring()返回指定索引区间的子串
```javascript
var s = 'hello, world'
s.substring(0, 5); // 从索引0开始到5（不包括5），返回'hello'
s.substring(7); // 从索引7开始到结束，返回'world'
```
### array
```javascript
var arr = [1, 2, 3];
arr.length; // 3
arr.length = 6;
arr; // arr变为[1, 2, 3, undefined, undefined, undefined]
arr.length = 2;
arr; // arr变为[1, 2]
```
```javascript
var arr = [1, 2, 3];
arr[5] = 'x';
arr; // arr变为[1, 2, 3, undefined, undefined, 'x']
```
#### indexof()



```javascript
var arr = [10, 20, '30', 'xyz'];
arr.indexOf(10); // 元素10的索引为0
arr.indexOf(20); // 元素20的索引为1
arr.indexOf(30); // 元素30没有找到，返回-1
arr.indexOf('30'); // 元素'30'的索引为2
```

#### slice
slice()就是对应String的substring()版本，它截取Array的部分元素，然后返回一个新的Array：
```javascript
var arr = ['A', 'B', 'C', 'D', 'E', 'F', 'G'];
arr.slice(0, 3); // 从索引0开始，到索引3结束，但不包括索引3: ['A', 'B', 'C']
arr.slice(3); // 从索引3开始到结束: ['D', 'E', 'F', 'G']

var arr = ['A', 'B', 'C', 'D', 'E', 'F', 'G'];
var aCopy = arr.slice();
aCopy; // ['A', 'B', 'C', 'D', 'E', 'F', 'G']
aCopy === arr; // false
```
#### push和pop
push()向Array的末尾添加若干元素，pop()则把Array的最后一个元素删除掉：
```javascript
var arr = [1, 2];
arr.push('A', 'B'); // 返回Array新的长度: 4
arr; // [1, 2, 'A', 'B']
arr.pop(); // pop()返回'B'
arr; // [1, 2, 'A']
arr.pop(); arr.pop(); arr.pop(); // 连续pop 3次
arr; // []
arr.pop(); // 空数组继续pop不会报错，而是返回undefined
arr; // []
```
#### unshift和shift
如果要往Array的头部添加若干元素，使用unshift()方法，shift()方法则把Array的第一个元素删掉：

#### sort()
#### reverse()
#### splice()

```javascript
var arr = ['Microsoft', 'Apple', 'Yahoo', 'AOL', 'Excite', 'Oracle'];
// 从索引2开始删除3个元素,然后再添加两个元素:
arr.splice(2, 3, 'Google', 'Facebook'); // 返回删除的元素 ['Yahoo', 'AOL', 'Excite']
arr; // ['Microsoft', 'Apple', 'Google', 'Facebook', 'Oracle']
// 只删除,不添加:
arr.splice(2, 2); // ['Google', 'Facebook']
arr; // ['Microsoft', 'Apple', 'Oracle']
// 只添加,不删除:
arr.splice(2, 0, 'Google', 'Facebook'); // 返回[],因为没有删除任何元素
arr; // ['Microsoft', 'Apple', 'Google', 'Facebook', 'Oracle']
```
#### contact
```javascript
var arr = ['A', 'B', 'C'];
var added = arr.concat([1, 2, 3]);
added; // ['A', 'B', 'C', 1, 2, 3]
arr; // ['A', 'B', 'C']



var arr = ['A', 'B', 'C'];
arr.concat(1, 2, [3, 4]); // ['A', 'B', 'C', 1, 2, 3, 4]
```
#### join

join()方法是一个非常实用的方法，它把当前Array的每个元素都用指定的字符串连接起来，然后返回连接后的字符串：
```javascript
var arr = ['A', 'B', 'C', 1, 2, 3];
arr.join('-'); // 'A-B-C-1-2-3'
```
### 对象
xiaohong的属性名middle-school不是一个有效的变量，就需要用''括起来。访问这个属性也无法使用.操作符，必须用['xxx']来访问：
```javascript
var xiaohong = {
    name: '小红',
    'middle-school': 'No.1 Middle School'
};
xiaohong['middle-school']; // 'No.1 Middle School'
xiaohong['name']; // '小红'
xiaohong.name; // '小红'
console.log(xiaoming.age); // undefined
xiaoming.age = 18; // 新增一个age属性
xiaoming.age; // 18
delete xiaoming.age; // 删除age属性
xiaoming.age; // undefined
'name' in xiaoming; // true
'grade' in xiaoming; // false
delete xiaoming['name']; // 删除name属性
xiaoming.name; // undefined
delete xiaoming.school; // 删除一个不存在的school属性也不会报错
//因为toString定义在object对象中，而所有对象最终都会在原型链上指向object，所以xiaoming也拥有toString属性。
要判断一个属性是否是xiaoming自身拥有的，而不是继承得到的，可以用hasOwnProperty()方法：
'toString' in xiaoming; // true
xiaoming.hasOwnProperty('toString'); // false
```
### 条件判断
在多个if...else...语句中，如果某个条件成立，则后续就不再继续判断了。
```javascript
var age = 20;
if (age >= 6) {
    console.log('teenager');
} else if (age >= 18) {
    console.log('adult');
} else {
    console.log('kid');
}
//输出teenager
```
### 循环
```jacascript
var o = {
    name: 'Jack',
    age: 20,
    city: 'Beijing'
};
for (var key in o) {
    console.log(key); // 'name', 'age', 'city'
}
```
### map和set
```javascrtpt
var m = new Map(); // 空Map
m.set('Adam', 67); // 添加新的key-value
m.set('Bob', 59);
m.has('Adam'); // 是否存在key 'Adam': true
m.get('Adam'); // 67
m.delete('Adam'); // 删除key 'Adam'
m.get('Adam'); // undefined
```

```javascript
var s1 = new Set(); // 空Set
var s2 = new Set([1, 2, 3]); // 含1, 2, 3

var s = new Set([1, 2, 3, 3, '3']);
s; // Set {1, 2, 3, "3"}


var s = new Set([1, 2, 3]);
s; // Set {1, 2, 3}
s.delete(3);
s; // Set {1, 2}
```
### iterable
S6标准引入了新的iterable类型，Array、Map和Set都属于iterable类型。
```javascript
var a = ['A', 'B', 'C'];
a.forEach(function (element, index, array) {
    // element: 指向当前元素的值
    // index: 指向当前索引
    // array: 指向Array对象本身
    console.log(element + ', index = ' + index);
});

```
## 函数
赠送函数arguments
vaScript还有一个免费赠送的关键字arguments，它只在函数内部起作用，并且永远指向当前函数的调用者传入的所有参数。arguments类似Array但它不是一个Array：
```javascript
function foo(x) {
    console.log('x = ' + x); // 10
    for (var i=0; i<arguments.length; i++) {
        console.log('arg ' + i + ' = ' + arguments[i]); // 10, 20, 30
    }
}
foo(10, 20, 30);
```
结构肤质，同时对多个变量赋值

```javscript
var [x, y, z] = ['hello', 'JavaScript', 'ES6'];

var x=1, y=2;
[x, y] = [y, x]//交换x,y的值

var {hostname:domain, pathname:path} = location;
//使用场景


function buildDate({year, month, day, hour=0, minute=0, second=0}) {
    return new Date(year + '-' + month + '-' + day + ' ' + hour + ':' + minute + ':' + second);
}
buildDate({ year: 2017, month: 1, day: 1 });
// Sun Jan 01 2017 00:00:00 GMT+0800 (CST)
buildDate({ year: 2017, month: 1, day: 1, hour: 20, minute: 15 });
// Sun Jan 01 2017 20:15:00 GMT+0800 (CST)
```
###方法
```javascript
'use strict';

var xiaoming = {
    name: '小明',
    birth: 1990,
    age: function () {
        var that = this; // 在方法内部一开始就捕获this
        function getAgeFromBirth() {
            var y = new Date().getFullYear();
            return y - that.birth; // 用that而不是this
        }
        return getAgeFromBirth();
    }
};
xiaoming.age(); // 25
```
### 装饰器
```javascript
'use strict';

var count = 0;
var oldParseInt = parseInt; // 保存原函数

window.parseInt = function () {
    count += 1;
    return oldParseInt.apply(null, arguments); // 调用原函数
};
```
### map and reduce
```javascript
var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9];
arr.map(String); // ['1', '2', '3', '4', '5', '6', '7', '8', '9']

var arr = [1, 3, 5, 7, 9];
arr.reduce(function (x, y) {
    return x + y;
}); // 25  求array的和

function(arr){//['adam', 'LISA', 'barT']，输出：['Adam', 'Lisa', 'Bart']
	return arr.map(x=>{return x[0].toUpperCase()+x.substr(1).toLowerCase()});
}
```
### filter
```javascript
var arr = [1, 2, 4, 5, 6, 9, 10, 15];
var r = arr.filter(function (x) {
    return x % 2 !== 0;
});
r; // [1, 5, 9, 15]

arr = ['apple', 'strawberry', 'banana', 'pear', 'apple', 'orange', 'orange', 'strawberry'];
r = arr.filter(function (element, index, self) {
    return self.indexOf(element) === index;
});//出去重复元素，indexof总是返回一个元素的位置

return arr.filter(function(x){for(var i=2;i<x;i++){if(x%i===0){return false;}}if(i===x){return true;}});
//筛选出素数
```
### sort
```javascript
var arr = [10, 20, 1, 2];
arr.sort(function (x, y) {
    if (x < y) {
        return -1;
    }
    if (x > y) {
        return 1;
    }
    return 0;
});
console.log(arr); // [1, 2, 10, 20]

//排序应该忽略大小写，按照字母序排序
var arr = ['Google', 'apple', 'Microsoft'];
arr.sort(function (s1, s2) {
    x1 = s1.toUpperCase();
    x2 = s2.toUpperCase();
    if (x1 < x2) {
        return -1;
    }
    if (x1 > x2) {
        return 1;
    }
    return 0;
}); // ['apple', 'Google', 'Microsoft']

```
### every and find
every()方法可以判断数组的所有元素是否满足测试条件。
```javascript
var arr = ['Apple', 'pear', 'orange'];
console.log(arr.every(function (s) {
    return s.length > 0;
})); // true, 因为每个元素都满足s.length>0

console.log(arr.every(function (s) {
    return s.toLowerCase() === s;
})); // false, 因为不是每个元素都全部是小写

//find()方法用于查找符合条件的第一个元素，如果找到了，返回这个元素，否则，返回undefined：
//findIndex()和find()类似，也是查找符合条件的第一个元素，不同之处在于findIndex()会返回这个元素的索引，如果没有找到，返回-1：
var arr = ['Apple', 'pear', 'orange'];
console.log(arr.find(function (s) {
    return s.toLowerCase() === s;
})); // 'pear', 因为pear全部是小写

console.log(arr.find(function (s) {
    return s.toUpperCase() === s;
})); // undefined, 因为没有全部是大写的元素

//forEach()和map()类似，它也把每个元素依次作用于传入的函数，但不会返回新的数组。forEach()常用于遍历数组，因此，传入的函数不需要返回值：
var arr = ['Apple', 'pear', 'orange'];
arr.forEach(console.log); // 依次打印每个元素

```
### 闭包//没看懂，以后有时间看
### 箭头函数
```javascript
x => x * x;
//等价于以下函数
function (x) {
    return x * x;
}

// 两个参数:
(x, y) => x * x + y * y

// 无参数:
() => 3.14

// 可变参数:
(x, y, ...rest) => {
    var i, sum = x + y;
    for (i=0; i<rest.length; i++) {
        sum += rest[i];
    }
    return sum;
}




x => ({ foo: x })

```
## 面向对象
```javascript
class Student {
    constructor(name) {
        this.name = name;
    }

    hello() {
        alert('Hello, ' + this.name + '!');
    }
}


class PrimaryStudent extends Student {
    constructor(name, grade) {
        super(name); // 记得用super调用父类的构造方法!
        this.grade = grade;
    }

    myGrade() {
        alert('I am at grade ' + this.grade);
    }
}

```
## 浏览器
### 浏览器对象
#### window
window对象有innerWidth和innerHeight属性，可以获取浏览器窗口的内部宽度和高度。内部宽高是指除去菜单栏、工具栏、边框等占位元素后，用于显示网页的净宽高。
对应的，还有一个outerWidth和outerHeight属性，可以获取浏览器窗口的整个宽高。
#### navigator
navigator对象表示浏览器的信息，最常用的属性包括：

navigator.appName：浏览器名称；
navigator.appVersion：浏览器版本；
navigator.language：浏览器设置的语言；
navigator.platform：操作系统类型；
navigator.userAgent：浏览器设定的User-Agent字符串。
#### screen
screen对象表示屏幕的信息，常用的属性有：

screen.width：屏幕宽度，以像素为单位；
screen.height：屏幕高度，以像素为单位；
screen.colorDepth：返回颜色位数，如8、16、24。
#### location
可以用location.href获取。要获得URL各个部分的值，可以这么写：

location.protocol; // 'http'
location.host; // 'www.example.com'
location.port; // '8080'
location.pathname; // '/path/index.html'
location.search; // '?a=1&b=2'
location.hash; // 'TOP'
#### document
```javascript
// 获取<p id="p-id">...</p>
var p = document.getElementById('p-id');
// 设置文本为abc:
p.innerHTML = 'ABC'; // <p id="p-id">ABC</p>
p.style.fontSize = '20px';
list.appendChild(js);
//创建新节点
haskell = document.createElement('p');
haskell.id = 'haskell';
haskell.innerText = 'Haskell';
//如果我们要把子节点插入到指定的位置怎么办？可以使用parentElement.insertBefore(newElement, referenceElement);，子节点会插入到referenceElement之前。

//删除DOM

/ 拿到待删除节点:
var self = document.getElementById('to-be-removed');
// 拿到父节点:
var parent = self.parentElement;
// 删除:
var removed = parent.removeChild(self);
removed === self; // true

//学习到了操作表单
```
# jquery
```JavaScript
        console.log("我" + $.fn.jquery);
        var pelement = $('#test-error');
        var ps = $('p'); // 返回所有<p>节点;
        var a = $('.red'); // 所有节点包含`class="red"`都将返回
        var a = $('.red.green'); // 注意没有空格！
        // 符合条件的节点：
        // <div class="red green">...</div>
        // <div class="blue green red">...</div>
        var email = $('[name=email]'); // 找出<??? name="email">
        var icons = $('[name^=icon]'); // 找出所有name属性值以icon开头的DOM
        $('form[name=upload] input'); //把选择范围限定在name属性为upload的表单里。如果页面有很多表单，其他表单的<input>不会被选择。
        $('form.test p input'); // 在form表单选择被<p>包含的<input>
```
```html
<!-- HTML结构 -->
<div class="testing">
    <ul class="lang">
        <li class="lang-javascript">JavaScript</li>
        <li class="lang-python">Python</li>
        <li class="lang-lua">Lua</li>
    </ul>
</div>
```
```javascript        
        $('ul.lang>li.lang-javascript'); // 可以选出[<li class="lang-javascript">JavaScript</li>]


        $('ul.lang li'); // 选出JavaScript、Python和Lua 3个节点

        $('ul.lang li:first-child'); // 仅选出JavaScript
        $('ul.lang li:last-child'); // 仅选出Lua
        $('ul.lang li:nth-child(2)'); // 选出第N个元素，N从1开始
        $('ul.lang li:nth-child(even)'); // 选出序号为偶数的元素
        $('ul.lang li:nth-child(odd)'); // 选出序号为奇数的元素        
        $('div:visible'); // 所有可见的div
        $('div:hidden'); // 所有隐藏的div
```
```html
<!-- HTML结构 -->
<ul class="lang">
    <li class="js dy">JavaScript</li>
    <li class="dy">Python</li>
    <li id="swift">Swift</li>
    <li class="dy">Scheme</li>
    <li name="haskell">Haskell</li>
</ul>
```
```JavaScript
var ul = $('ul.lang'); // 获得<ul>
var dy = ul.find('.dy'); // 获得JavaScript, Python, Scheme
var swf = ul.find('#swift'); // 获得Swift
var hsk = ul.find('[name=haskell]'); // 获得Haskell

var swf = $('#swift'); // 获得Swift
var parent = swf.parent(); // 获得Swift的上层节点<ul>
var a = swf.parent('.red'); // 获得Swift的上层节点<ul>，同时传入过滤条件。如果ul不符合条件，返回空jQuery对象



var swift = $('#swift');

swift.next(); // Scheme
swift.next('[name=haskell]'); // 空的jQuery对象，因为Swift的下一个元素Scheme不符合条件[name=haskell]

swift.prev(); // Python
swift.prev('.dy'); // Python，因为Python同时符合过滤器条件.dy

var langs = $('ul.lang li'); // 拿到JavaScript, Python, Swift, Scheme和Haskell
var a = langs.filter('.dy'); // 拿到JavaScript, Python, Scheme

var langs = $('ul.lang li'); // 拿到JavaScript, Python, Swift, Scheme和Haskell
langs.filter(function () {
    return this.innerHTML.indexOf('S') === 0; // 返回S开头的节点
}); // 拿到Swift, Scheme

var langs = $('ul.lang li'); // 拿到JavaScript, Python, Swift, Scheme和Haskell
var arr = langs.map(function () {
    return this.innerHTML;
}).get(); // 用get()拿到包含string的Array：['JavaScript', 'Python', 'Swift', 'Scheme', 'Haskell']

var langs = $('ul.lang li'); // 拿到JavaScript, Python, Swift, Scheme和Haskell
var js = langs.first(); // JavaScript，相当于$('ul.lang li:first-child')
var haskell = langs.last(); // Haskell, 相当于$('ul.lang li:last-child')
var sub = langs.slice(2, 4); // Swift, Scheme, 参数和数组的slice()方法一致
```

```html
<form id="test-form" action="#0" onsubmit="return false;">
    <p><label>Name: <input name="name"></label></p>
    <p><label>Email: <input name="email"></label></p>
    <p><label>Password: <input name="password" type="password"></label></p>
    <p>Gender: <label><input name="gender" type="radio" value="m" checked> Male</label> <label><input name="gender" type="radio" value="f"> Female</label></p>
    <p><label>City: <select name="city">
        <option value="BJ" selected>Beijing</option>
        <option value="SH">Shanghai</option>
        <option value="CD">Chengdu</option>
        <option value="XM">Xiamen</option>
    </select></label></p>
    <p><button type="submit">Submit</button></p>
</form>

```
```javascript
//输入值后，用jQuery获取表单的JSON字符串，key和value分别对应每个输入的name和相应的value，例如：{"name":"Michael","email":...}
var json = null;
var obj = {};
// 限定状态:input 可获取：<input>，<textarea>，<select>和<button> 元素
$('#test-form :input').filter
(
    function()
    {
      // 过滤节点数组中：未选中的radio单选框节点和submit按钮节点
      // this是DOM对象，获取节点属性type、checked等
       var isNotChecked  = this.type === 'radio' && !this.checked;
       if( isNotChecked  || this.type === 'submit')
            return false;
       else
            return true;
    }
).map
(
    function()
    {
       // select元素可直接获取name属性和选中的值
       return obj[this.name] = this.value;
    }
)
json = JSON.stringify(obj,null,'  ');

var div = $('#test-div');
div.css('color'); // '#000033', 获取CSS属性
div.css('color', '#336699'); // 设置CSS属性
div.css('color', ''); // 清除CSS属性


var div = $('#test-div');
div.hasClass('highlight'); // false， class是否包含highlight
div.addClass('highlight'); // 添加highlight这个class
div.removeClass('highlight'); // 删除highlight这个class

// 浏览器可视窗口大小:
$(window).width(); // 800
$(window).height(); // 600

// HTML文档大小:
$(document).width(); // 800
$(document).height(); // 3500

// 某个div的大小:
var div = $('#test-div');
div.width(); // 600
div.height(); // 300
div.width(400); // 设置CSS属性 width: 400px，是否生效要看CSS是否有效
div.height('200px'); // 设置CSS属性 height: 200px，是否生效要看CSS是否有效
```
attr()和removeAttr()方法用于操作DOM节点的属性：
```javascript
// <div id="test-div" name="Test" start="1">...</div>
var div = $('#test-div');
div.attr('data'); // undefined, 属性不存在
div.attr('name'); // 'Test'
div.attr('name', 'Hello'); // div的name属性变为'Hello'
div.removeAttr('name'); // 删除name属性
div.attr('name'); // undefined
```

对于表单元素，jQuery对象统一提供val()方法获取和设置对应的value属性：
```javascript
/*
    <input id="test-input" name="email" value="">
    <select id="test-select" name="city">
        <option value="BJ" selected>Beijing</option>
        <option value="SH">Shanghai</option>
        <option value="SZ">Shenzhen</option>
    </select>
    <textarea id="test-textarea">Hello</textarea>
*/
var
    input = $('#test-input'),
    select = $('#test-select'),
    textarea = $('#test-textarea');

input.val(); // 'test'
input.val('abc@example.com'); // 文本框的内容已变为abc@example.com

select.val(); // 'BJ'
select.val('SH'); // 选择框已变为Shanghai

textarea.val(); // 'Hello'
textarea.val('Hi'); // 文本区域已更新为'Hi'
```

```javascript
function hello() {
    alert('hello!');
}

a.click(hello); // 绑定事件

// 10秒钟后解除绑定:
setTimeout(function () {
    a.off('click', hello);
}, 10000);

//监控文本框内容改动                        
var input = $('#test-input');
input.change(function () {
    console.log('changed...');
});



$('#submit').click(function () {
    //此代码必须在用户触发下才能执行
    setTimeout(function(){window.open('/');},3000);
});
```
### 动画

toggle()方法则根据当前状态决定是show()还是hide()

show()和hide()是从左上角逐渐展开或收缩的，
而slideUp()和slideDown()则是在垂直方向逐渐展开或收缩的。

slideToggle()则根据元素是否可见来决定下一步动作：

fadeIn()和fadeOut()的动画效果是淡入淡出，也就是通过不断设置DOM元素的opacity属性来实现，而fadeToggle()则根据元素是否可见来决定下一步动作：
animate()还可以再传入一个函数，当动画结束时，该函数将被调用：
```JavaScript
var div = $('#test-animate');
div.animate({
    opacity: 0.25,
    width: '256px',
    height: '256px'
}, 3000, function () {
    console.log('动画已结束');
    // 恢复至初始状态:
    $(this).css('opacity', '1.0').css('width', '128px').css('height', '128px');
});


```
jQuery的动画效果还可以串行执行，通过delay()方法还可以实现暂停，这样，我们可以实现更复杂的动画效果，而代码却相当简单：
```javascript
var div = $('#test-animates');
// 动画效果：slideDown - 暂停 - 放大 - 暂停 - 缩小
div.slideDown(2000)
   .delay(1000)
   .animate({
       width: '256px',
       height: '256px'
   }, 2000)
   .delay(1000)
   .animate({
       width: '128px',
       height: '128px'
   }, 2000);
}
</script>
```

### 拓展
编写jQuery插件
给jQuery对象绑定一个新方法是通过扩展$.fn对象实现的。让我们来编写第一个扩展——highlight1()：
```javascript
$.fn.highlight1 = function () {
    // this已绑定为当前jQuery对象:
    this.css('backgroundColor', '#fffceb').css('color', '#d85030');
    return this;
    //为什么最后要return this;？因为jQuery对象支持链式操作，我们自己写的扩展方法也要能继续链式下去：$('span.hl').highlight1().slideDown();
}
```


```javascript
$.fn.highlight = function (options) {
    // 合并默认值和用户设定值:
    var opts = $.extend({}, $.fn.highlight.defaults, options);
    this.css('backgroundColor', opts.backgroundColor).css('color', opts.color);
    return this;
}

// 设定默认值:
$.fn.highlight.defaults = {
    color: '#d85030',
    backgroundColor: '#fff8de'
}
```
最终，我们得出编写一个jQuery插件的原则：

- 给$.fn绑定函数，实现插件的代码逻辑；
- 插件函数最后要return this;以支持链式调用；
- 插件函数要有默认值，绑定在$.fn.<pluginName>.defaults上；
- 用户在调用时可传入设定值以便覆盖默认值。

# 错误处理
```javascript
var r, n, s;
try {
    s = prompt('请输入一个数字');
    n = parseInt(s);
    if (isNaN(n)) {
        throw new Error('输入错误');
    }
    // 计算平方:
    r = n * n;
    console.log(n + ' * ' + n + ' = ' + r);
} catch (e) {
    console.log('出错了：' + e);
}

```



# JavaScript 笔记

## JavaScript 布局

- 通常 JavaScript 代码可以放到 `<head> </head>` 中；

    ```javascript
    <html>
        <head>
            <script type="text/javascript">
                alert('Hello World');
            </script>
        </head>
        <body>
            ...
        </body>
    </html>
    ```

    > `type` 默认属性即为：`JavaScript`, 所以可以不必显示指定。

- 将 JavaScript 代码放到单独的 `.js` 文件中；

    ```javascript
    <html>
        <head>
            <script src="/static/js/abc.js"></script>
        </head>
        <body>
            ...
        </body>
    </html>
    ```

## JavaScript 基础

### 比较运算符

`==` ： 自动转换数据类型在比较；
`===` ： 如果数据类型不一致，返回 `false`；

### 字符串

使用 \`xxxxxxx\` 标识多行字符串：

```javascript
console.log(`Hello
World
!`);
```

可以用 `{$variable}` 替换字符串中的变量：

```javascript
var name = 'Bob';
var age = 20;
console.log(`Hello, ${name}, you are ${age} years old!`);
```

对字符串的操作本身不会改变自身，而是返回一个新的字符串；

`str.toUpperCase()` - 转变为大写
`str.toLowerCase()` - 转变为小写
`str.indexOf('string')` - 获取指定字符串出现的位置
`str.substring(startIndex, length)` - 获取截取的字符串

### 数组

通过索引进行赋值可以直接修改这个 Array：

```javascript
var arr = ['A', 'B', 'C'];
arr[1] = 100;
arr; //arr now is ['A', 100, 'C'];
```

`indexOf(value)` - 搜索指定值的索引；
`slice(startIndex, length)` - 类似于 String 的 `substring()`；
`push('value1', 'value2')` - 末尾添加值；
`pop()` - 删除最有一个值；
`sort()` - 排序；
`reverse()` - 反转数组；
`splice(startIndex, deleteNum, replaceValue1, replaceValue2)` - 从指定的索引开始删除若干值，然后再从该位置添加若干值；
`concat(newArray)` - 连接两个 Array;
`join(connectValue)` - 每个值用指定的字符串连接，返回一个连接后的字符串

### 对象

JavaScript 对象是动态类型，可以添加或删除属性;

```javascript
var person = {
    name: 'David',
    age: '20',
};

person.gender = 'male'; // 新增 gender 属性
delete person.age; // 删除 age 属性
```

使用 `in`/`hasOwnProperty()` 检测是否拥有某属性：

`in` - 包括继承的属性, 例如： `toString` 是 `object` 对象的属性，结果也是 `true`;
`hasOwnProperty()` - 必须是自身拥有的属性

```javascript
'age' in person; //true
'birth' in person; //false
person.hasOwnProperty('age'); //true
person.hasOwnProperty('toString'); //true
```

### 循环

- `for(i=index; i<length; i++)`;
- `for (var key in object)`;
- `while(condition)`;
- `do {...} while(condition)`;

### Map & Set

`Map` - 键值对集合；

```javascript
var m = new Map([['David', 100], ['Bob', 10]]);
m.get('David'); //100
m.set('Adam', 99); //添加新的 key-value
m.has('Bob'); //true
m.delete('Adam') //删除 key-'Adam'
```

`Set` - Key 的集合，Key 不能重复，没有索引；

```javascript
var s = new Set([1, 2, 3, 3, '3']);
s.add(4); // Set {1, 2, 3, '3', 4}
s.delete(3); // Set {1, 2, '3', 4}
```

### iterable

新的 `iterable` 类型，`Array`、`Map` 和 `Set` 都属于 `iterable` 类型。

`for ... of` 循环 解决 `for ... in` 循环的历史遗留问题:

```javascript
var a = ['A', 'B', 'C'];
a.name = 'David';
for (var i in a) {
    console.log(i); // '0', '1', '2', 'name'
}
for (var i of a) {
    console.log(i); // 'A', 'B', 'C'
}

a.forEach(function (element, index, array) {
    // element: 指向当前元素的值；
    // index：指向当前索引；
    // array：指向 Array 对象本身
})
```

## 函数

2 种定义方法：

- `function abs(x) { ... }`
- `var abs = function(x) { ... };`

参数：

- `arguments` - 用于函数内部，指向传入的所有参数
- `...rest` - 指向传入的未显示指定的参数 `function foo(a, b, ...rest){ ... }`

### 作用域

JavaScript 默认有一个全局对象 `window`，任何全局变量（函数也视为变量）都会绑定到 `window` 上。

`var` - 定义**局部**作用域变量
`let` - 定于**块**级作用域变量

```javascript
function foo() {
    for (let i=0; i<100; i++) {
        //
    }
    i += 100; // SyntaxError;

    for (var i=0; i<100; i++) {
        //
    }
    i += 100; // 仍然可以引用变量i
}
```

`const` - 常量

### 解构赋值

可以同时赋值多个变量，包括嵌套的数组：

`let [x, [y, z]] = ['hello', ['hi', 'welcome']];`

对象赋值：

```javascript
var person = {
    name: 'David',
    age: 20,
    gender: 'male',
    passport: 'G-12345678',
    address: {
        city: 'Beijing',
        zipcode: '100001'
    }
};
var {name, address: {city, zip}} = person;
name; // 'David'
city; // 'Beijing'
zip; // undefined, 因为属性名是zipcode而不是zip
// 注意: address不是变量，而是为了让city和zip获得嵌套的address对象的属性:
address; // Uncaught ReferenceError: address is not defined
```

## 高阶函数

可以将函数作为参数传入：

```javascript
function add(x, y, abs) {
    return abs(x) + abs(y);
}
```

### map 方法

`arr.map(function (x) { return abs(x); } )` - 依次对数组的每个元素调用指定的函数：

```javascript
function pow(x) {
    return x * x;
}
var arr = [1, 2, 3, 4, 5];
arr.map(pow); // [2, 4, 9, 16, 25]

arr.map(function (x) { return x * x; }); // [2, 4, 9, 16, 25]

arr.map(x => x * x); // [2, 4, 9, 16, 25]
```

### reduce 方法

`arr.reduce(function (x, y) { return add(x, y); })` - 分别对数组的进行函数调用，依次往后累计：

```javascript
var arr = [1, 2, 3, 4, 5];
arr.reduce( function (x, y) { return x + y; }); // 15

arr.reduce( (x,y) => x * y; ) // 15
```

### filter 方法

`arr.filter(function (x) { return x>99 })` - 通过返回值决定是否保留该元素

### sort 方法

`arr.sort()` - 默认排序按字符串 ASCII 码进行排序（eg. 10 < 2）

`arr.sort(function(x,y) { if (x < y) return -1; else if (x > y) return 1; else return 0;})` - 修改排序规则则可以按照数字大小进行排序

`sort` 方法直接对当前 Array 进行修改。

### every 方法

判断 Array 中的每个元素是否满足条件

`let r = arr.every(funciton (s) { return s.length > 0;});` - 判断 Array 中是否存在空元素

### find\findIndex 方法

查找 Array 中满足条件的第一个元素\索引

`let s = arr.find(function (s) { return s.toLowerCase() === s });` - 返回第一个小写的元素，如果未找到返回 `undefinded`

### foreach 方法

用于遍历 Array, 没有返回值，也不会改变原 Array, 常用于遍历

`arr.forEach(console.log)`

## 闭包

将函数作为结果返回。实现一个计数器的示例：

```javascript
function counter (initial) {
    var x = initial || 0;
    return function() return x ++;
}

var c = conter(100);
c(); //100
c(); //101
```

## 箭头函数

```javascript
(x, y) => x * y;
```

==> 等价于 ==>

```javascript
function (x, y) {
    return x * y;
}
```

## generator 生成器

类似于在一个函数内可以返回多个结果

```javascript
function* name(max) {
    var index = 0;
    while(index < max) {
        yield index++;
    }
    return index;
}

for (var x of name()) {
    console.log(x);
}
```

## 标准对象

`number`, `string`, `boolean`, `function`, `underfined`, `object` - (`Array`, `null` 均属于 `object`）

### Date

`var date = new Date(2019, 6, 12);` - 2019/07/12

JavaScript 的 Date 对象月份值从 0 开始，牢记 0=1 月，1=2 月，2=3 月，……，11=12 月。

### RegExp

#### 正则表达式基础
在js中，正则表达式常常用于匹配字符串，它可以实现很多方法无法实现的功能。下面介绍js中正则表达式修饰符（i、g、m）使用。
通过i修饰符的设置，忽略大小写
在正则表达式后面加上g修饰符，查找字符串中所有匹配到的字符。
m修饰符。在正则表达式后面加上m修饰符，可以实现在多行字符中匹配字符，而g修饰符只能实现单行匹配。

`\d` - 数字
`\w` - 字母或数字
`\s` - 空格

`.` - 任意字符
`*` - 任意个字符(包括 0 个)
`+` - 至少一个字符
`?` - 0 或 1 个字符
`{n}` - n 个字符
`{n, m}` - n~m 个字符

`[]` - 表示范围
`[0-9a-zA-Z]` - 数字及字母
`A|B` - A 或 B
`^` - 以...开头
`$` - 以...结尾

`()` - 定义组

#### RegExp

`test()` 方法测试字符串是否符合正则表达式

```javascript
var re = new RegExp('^\d{3}\-\d{3-8}$');
var re = /^\d{3}\-\d{3-8}$/;

re.test('010-12345'); // true
```

`exec()` 方法提取正则表达式中定义的组, 失败返回 null

```javascript
var re = /^(\d{3})-(\d{3,8})$/;
re.exec('010-12345'); // ['010-12345', '010', '12345']
re.exec('010 12345'); // null
```

```javascript
var re = /^[0-9a-zA-Z\.]+@.+\.\w+$/; // 匹配邮箱 v-tawe@microsoft.com

var re = /^\<(.+)\>\s+([0-9a-zA-Z\.]+@.+\.\w+)$/; // 匹配带名字的邮箱 <David Tang> v-tawe@microsoft.com
```

#### JSON

序列化 - `JSON.parse('json')`
反序列化 - `JSON.stringify(obj)`

## 面向对象

两种创建对象的方式：

通过数据类型对象创建：

```javascript
var Student = {
    name: 'Robot';
    height: 1.2;
    run: function() {
        return this.name + 'is running';
    }
}

function createStudent(name) {
    var s = Object.create(Student);
    s.name = name;
    return s;
}

var xiaoming = createStudent('xiaoming');
xiaoming.run(); //xiaoming is runing
```

通过构造函数实现：

```javascript
function Student(props) {
    this.name = props.name || 'Robot';
    this.height  = props.height || '1.2';
}

Student.prototype.run = function() {
    return this.name + 'is running';
}

function createStudent(props) {
    return new Student(props || {})
}
```

通过 class 实现：

```javascript
class Student {
    constructor(name) {
        this.name = name;
    }

    run() {
        return this.name + 'is running';
    }
}
```

### 原型继承

定义新的构造函数，并在内部调用继承的构造函数的 `call()` 方法绑定`this`;

![inherits](./img/inherits.png)

只有函数才有 `prototype` 属性, `_proto_` 是所有对象都有的（包括函数）, 即对象原型 `xxx.constructor`。

通过构造函数实现继承：

```javascript
function inherits(Child, Father) {
    var F = function(){};
    F.prototype = Father.prototype;
    Child.prototype = new F();
    Child.prototype.constructor = Child;
}

function Student(props) {
    this.name = props.name || 'unnamed';
    this.height = props.height || 1.2;
}

Student.prototype.run = function() {
    return this.name + 'is running';
}

function PrimaryStudent(props) {
    Student.call(this, props);
    this.grade = props.grade || 1;
}

inherits(PrimaryStudent, Student);

PrimaryStudent.prototype.getGrade = function() {
    return this.grade;
}
```

通过 class 实现继承：

```javascript
class PrimaryStudent extends Student {
    constructor(props) {
        super(props);
        this.grade = props.grade || 1;
    }

    getGrade() {
        return this.grade;
    }
}
```

## 浏览器

需要支持 ES6

- 浏览器窗口： `windows`： `windows.innerWidth; windows.innerHeight`;
- 浏览器信息： `navigator`: `navigator.appName; navigator.appVersion`...;
- 屏幕信息： `screen`: `screen.width; screen.height`...;
- 当前页面 URL 信息: `location`: `location.protocol; location.host`...;
- DOM 对象: `document`: `document.title; document.cookie`...;
    - `document.getElementById();` - 根据 ID 获取 DOM 节点
    - `document.getElementsByTagName();` - 根据 Tag 名词获取 DOM 节点
    - `document.cookie` - 获取 cookie 信息，服务器端使用 `httpOnly` 可以禁止 JS 读取 Cookie;
- 浏览器历史： `history`: `history.back(); history.forward();` **历史遗留对象已弃用！！**

### DOM

```javascript

var d = document.getElementById('id');
document.getElementsByTagName('p');
document.getElementsByClassName('class');

document.querySelector('#id');
document.querySelectorAll('div.class > p');

d.children; // 获取 id 下的所有子节点
d.firstElementChild; // 获取 id 下的第一个子节点

// 更新 DOM
d.innerHTML = 'ABC <span style="color:red">RED</span> XYZ'; // 可以设置 HTML 标签
d.innerText = 'ABC XYZ';

//// 设置 CSS
d.style.color = '#ff0000';
d.style.fontSize = '20px';

// 插入 DOM
var div1 = document.createElement('p');
div1.id = 'div1';
div1.innerText = 'DIV1';
d.appendChild(div1);

var ref = document.getElementById('ref');
d.insertBefore(div1, ref);

// 删除 DOM
var parent = d.parentElement;
// 删除节点时 children 节点实时变化
parent.removeChild(parent.children[0]); // 删除节点 0
parent.removeChild(parent.children[0]); // 删除节点 1
```

### 表单

没有 `name` 属性的表单控件不会提交。

表单控件

- `<input type='text'></input>`
- `<input type='password'></input>`
- `<input type='radio'></input>`
- `<input type='checkbox'></input>`
- `<input type='hidden'></input>`
- `<select></select></input>`

获取值

- `text, password, hidden, select` 使用 `value` 获取值
- `select` 使用 `checked` 获取值

### 文件

`<input type='file'></input>`

### AJAX

只支持同源策略访问，跨域需要使用 CORS 策略。

1. 创建 `XMLHttpRequest` 对象；
1. 设置 `onreadystatechange` 回调函数；
1. 通过 `readyState === 4` 判断请求是否完成；
1. 根据 `status === 2000` 判断是否成功响应；
1. 调用 `open()` 方法, 参数1： `GET/POST`; 参数2： URL 地址； 参数3：是否异步（默认 true);
1. 调用 `send()` 方法发送请求；

```javascript
var request = new XMLHttpRequest(); // 新建 AJAX 对象

// 状态发生变化时，函数被回调
request.onreadystatechange = function() {
    if (request.readyState === 4) { // 成功
        // 判断响应结果
        if (request.status === 200) {
            // 成功，responseText - 响应文本
            return success(request.responseText);
        }
        else {
            // 失败
            return fail(request.status);
        }
    }
}

// 发送请求
request.open('GET', '/api/categories');
request.send();
```

## Promise

```javascript
function ajax(method, url, data) {
    var request = new XMLHttpRequest();
    return new Promise(function (resolve, reject) {
        request.onreadystatechange = function() {
            if (request.readyState === 4) {
                if (request.status === 200) {
                    resolve(request.responseText);
                }
                else {
                    reject(request.status);
                }
            }
        };
    request.open(method, url);
    request.send(data);
    });
}

var p = ajax('GET', '/api/categories');
p.then(function(text) {
    log.innerText = text;
}).catch(function(status) {
    log.innerText ='ERROR' + status;
})
```

并行执行： `Promise.all()`
容错执行： `Promise.race()`

```javascript
var p1 = new Promise(function(resolve, reject) {
    ...
})

var p2 = new Promise(function(resolve, reject) {
    ...
})

// p1, p2 均执行成功后，执行 then
Promise.all([p1, p2]).then(function(results) {
    console.log(results);
})

// p1, p2 同时执行，先执行成功的返回结果给 then，后执行成功的结果丢失
Promise.race([p1, p2]).then(function(result) {
    console.log(result);
})
```

## JQuery

- 按 ID 查找： `$('#id')`
- 按 class 查找： `$('.class')`
- 按 Tag 查找： `$('tag')`
- 按属性查找： `$('[name=email]')`; `$('[type=password]')`
    - `$('[name^=icon])`: 查找 name 属性以 icon 开头的 DOM;
    - `$('[name$=with]')`: 查找 name 属性以 with 结尾的 DOM;
- 组合查找： `$('input[name=email]')`; `$('tr.red')`
- 多项选择器： `$('p, div')`; `$('p.red, p.green')`; `$('input[name=email],[name=password]')`

### 选择器

- 层级选择器 用 空格 隔开： `$('ul li.class')`
- 子选择器 用 > 隔开： `$('ul > li.class')`

    层级选择器 和 子选择器的区别在： 子选择器必须时父子关系，不可跨层级选择！

- 过滤器 用 : 隔开： `$('ul li:first-child')`;  `$('ul li:last-child')`; `$('ul li:nth-child(2)')`; `$('ul li:nth-child(even)')`

### 表单相关

- `:input` - `<input>`, `<textarea>`, `<select>`, `<button>`
- `:file` - `input[type=file]`
- `:checkbox` - `input[type=checkbox]`
- `:radio` - `input[type=radio]`
- `:focus` - 获取鼠标当前的焦点控件 `input:focus`
- `:checked` - 已选择的单选或复选框控件 `input[type=radio]:checked`
- `:enabled` - 可以正常输入的控件
- `:disabled` - 已被禁用的控件
- `:visible` - 可见的控件
- `:hidden` - 隐藏的控件
- ... ...

### 查找 & 过滤

- `find()` - 在所有子节点中进行查找
- `parent()` - 从当前节点向上查找
- `next()` & `prev()` - 同一层级节点前后进行查找

- `filter()` - 过滤掉不符合条件的节点
- `map()` - 把一个 jQuery 对象包含的若干 DOM 节点转化为其他对象
- `first()` & `last()` & `slice(2, 4)` - 截取 jQuery 对象

### 操作

- `text()` & `html()` - 获取或修改 text 或 html
- `val()` - 获取或修改 value 属性
- `css()` - 获取或修改 css
- `hide()` & `show()` - 隐藏或显示元素; 增加参数可以实现淡入淡出效果： `hide('slow')` / `show('slow')`
- `attr()` & `removeAttr()` - 修改 DOM 属性
- `prop()` - 与 attr() 类似

- `append()` & `prepend()` - 添加 DOM 节点
- `before()` & `after()` - 在当前元素前/后插入 DOM 节点
- `remove()` - 删除节点

### 事件

绑定事件：

- `$('#id').on('click', function() { alert('Hello, World'); });`
- `$('#id').click(function() { alert('Hello, World'); });`

事件类型：

- `click` - 单击
- `dblclick` - 双击
- `mouseenter` - 鼠标移入
- `mouseleave` - 鼠标移除
- `mousemove` - 鼠标在 DOM 内移动
- `hover` - `mouseenter` + `mouseleave`

- `keydown` - 键盘按下
- `keyup` - 键盘松开
- `keypress` - 按一次键触发

- `focus` - DOM 获得焦点
- `blur` - DOM 失去焦点
- `change` - DOM 内容变更
- `submit` - form 提交
- `ready` - 页面载入并且 DOM 树初始化后 仅作用于 document 对象

    `$(document).ready(function() {...});` 
    简化后：
    `$(function() {...});`

- `off('click', <functionName>)` 取消事件绑定

### 动画效果

- `show('slow') / hide('slow') / toogle('slow')` - 左上角缓慢收缩
- `slideUp('slow') / SlideDown('slow') / slideToogle('slow')` - 垂直缓慢收缩
- `fadeIn('slow') / fadeOut('slow') / fadeToggle('slow')` - 淡入淡出
- `animate()` - 自定义效果

    ```javascript
    $('#id').animate({
        opacity: 0.25,
        width: 0px;
        height: 0px;
    }, 1000, function() { console.log('Complete'); }).delay(1000).animate(...);
    ```

    可以使用 `delay()` 实现动画的暂停。

### AJAX

- `$.ajax(async, method, contentType, data, headers, dataType)`
- `$.ajax(async, method, contentType, data, headers, dataType, jsonp:'callback', jsonpCallback:'callbackFunction', success: function(data){...})`

- `$.get(url)`
- `$.post(url, data)`

- `$.getJSON(url)`

### 扩展

1. 使用 `$.fn` 绑定函数
1. 使用 `return this` 实现链式调用
1. 插件有默认值，绑定在 `$.fn.<pluginName>.defaults` 上
1. 用户在调用时可传入参数以覆盖默认值

```javascript
$.fn.<pluginName> = function(options) {
    var bgcolor = options && options.bgcolor || '#FFFFFF';
    this.css('background', bgcolor)
    return this;
}
```

`extend(target, obj1, obj2, ...)` 会将靠后对象的值合并到第一个 target 中, 越往后面的对象优先级越高；

`extend({}, $.fn.<pluginName>.defaults, options)`

## 异常处理

使用 `try {...} catch {...} finally {...}` 捕获

> 注意：异步操作时的异常无法在调用处捕获，同样，对于控件的事件处理，在绑定事件的代码处无法捕获事件处理函数的异常。

## unerscore

与 jQuery 类似，提供一套完善的 API, 绑定到 `_` 变量上。

### Collections

#### map/filter

类似于 Array 的 `map/filter` 方法

- `_.map(object, function(value, key) {...});`
- `_.mapObject(object, function(value, key) {...});`
- `_.filter(object, function(value, key) {...});`

#### every/some

集合中元素都满足情况，`_.every()` 返回 `true`, 集合中部分元素满足情况， `_.some()` 返回 `true`

- `_.every([1, 4, 7, -3, -9], (x) => x > 0); // false`
- `_.some([1, 4, 7, -3, -9], (x) => x > 0); // true`

#### max/min

集合时 Object，会忽略掉 key，只比较 value

`_.max({ a: 1, b: 2, c: 3 }); // 3`

#### groupBy

`_.groupBy([1, 2, 3, 4, 5], (x) => { if(x<3) return 'small'; else return 'big' });`

更多 [underscrore 方法](https://underscorejs.org/)。


```javascript

            //alert('hello');
            //document.getElementById("parameter_list").style.display = "none";
            var a = 1;
            console.log(a);
            console.log(0 / 0);
            console.log('\u4e2d\u6587');
            console.log(`this
                            is
                    multiline str`);
            var xiaohong = {
                name: 'xiaohong',
                age: 18,
                'midle-school': 'no.1 school'
            };
            console.log(xiaohong['midle-school'])
            console.log(xiaohong.toString)


            var a = ['A', 'B', 'C'];
            var s = new Set(['A', 'B', 'C']);
            var m = new Map([[1, 'x'], [2, 'y'], [3, 'z']]);
            for (var x of a) { // 遍历Array
                console.log(x);
            }
            for (var x of s) { // 遍历Set
                console.log(x);
            }
            for (var x of m) { // 遍历Map
                console.log(x[0] + '=' + x[1]);
            }
            function checkform() {
                var username = document.getElementById("username");
                //alert("mog");
                var md5_pwd = document.getElementById('password');
                // 把用户输入的明文变为MD5:
                md5_pwd.value = toMD5(input_pwd.value);
                alert(username.value);
                console.log(username.value);
                return true;
            }
            var checkRegisterForm = function () {
                var r1 = /^[A-Za-z0-9]{3,10}$/;
                var r2 = /^\w{6-20}$/;
                var u = document.getElementById("username");
                var p1 = document.getElementById("password");
                var p2 = document.getElementById("password-2")
                if (r1.test(u.value)) {
                    return false;
                }
                if (!r2.test(p1.value) && !r2.test(p2.value)) {
                    return false;
                }
                if (p1.value != p2.value) {
                    return false;
                }
                return true;
            }
```