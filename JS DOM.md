[TOC]

## 语法
### 变量
- 变量名大小写敏感
- js不允许变量名包含空格或标点符号，允许包含字母，数字，美元符号，下划线。
### 数据类型
#### 字符串
- 字符串中包含单双引号时可以用反斜线\进行转义
`var mood='don\'t ask';`

- 单引号和双引号都可以包住字符串，不管使用双还是单，同个脚本中应保持一致
#### 布尔值
千万不要把布尔值用引号括起来，布尔值false与字符串值'false'是两码事
#### 数组
##### 数组声明
> 声明数组用中括号
声明对象用大括号

```javascript
var beatles=Array(4)
var beatles=Array()
var beatles=Array('John','Paul','George','Ringo')
var beatles=['John','Paul','George','Ringo']
var beatles=[ ]
```

- 不同数据类型的可以放进一个数组
`var lennon=['John',1940,false]`

- 数组元素可以是变量
```javascript
var name='John';
beatles[0]=name;
```

- 数组可以包含其他数组
```javascript
var lennon=['John',1940,false];
var beatles=[ ];
beatles[0]=lennon;
beatles[0][0]就是John字符串
```
#### 对象
##### 声明对象
```javascript
var lennon=Object();
lennon.name='John';
lennon.year=1940;
lennon.living=false;
var lennon={name:'John', year:1940, living:false};
var lennon={ };
```
### 条件语句
#### 比较操作符
- ===
严格比较，不仅比较值，还比较变量的类型

- !===
严格不相等
### 循环语句
#### while循环
while与if语句非常相似，它们的语法几乎完全一样
```javascript
while(condition){
statement;
}
```
小括号里的求值结果是TRUE，花括号里的代码就将反复执行。
#### do while
```javascript
do{
statements;
}while(condition);
```
### for循环
最常见的用途之一就是对某个数组里的全体元素进行遍历处理。
```javascript
for(var n=1; n＜11; n＋＋){
statements;
}
```
### 函数
### 对象
对象是一种数据类型，包含在对象里的数据可以通过两种形式访问，属性和方法。
- 属性是隶属于某个特定对象的变量
- 方法是只有某个特定对象才能调用的函数
对象就是由一些属性和方法组合在一起而构成的一个数据实体。
属性和方法都使用‘点’语法来访问：
```javascript
object.property
object.method( )
```
实例是对象的具体个体，你和我都是人，都可以用person对象来描述，但你和我是不同的个体，有不同的属性，年龄可能不同，因此，你和我对应着两个不同的person对象。
`var a=new Person;`
#### 内建对象
Array
Math
Date
#### 宿主对象
不是由JS语言本身而是由它运行环境提供的。具体到web应用，这个环境就是浏览器。由浏览器提供的预定义对象被称为宿主对象。
包括Form Image Element等。
document对象也能获得网页上的任何一个元素的信息。

## DOM
5个常用的DOM方法：
- getElementById
- getElementByTagName
- getElementByClassName
- getAttribute
- setAttribute
文档对象模型document object model
家谱树模型

### 节点
文档是由节点构成的集合，节点有很多类型，先看其中的三种：元素节点，文本节点，属性节点。
#### 元素节点
标签的名字就是元素的名字，元素可以包含其他元素。文档中每个元素节点都是一个对象。
#### 文本节点
比如p元素包含着文本节点。
#### 属性节点
比如 `title='model'`是一个属性节点
#### 获取元素
3种DOM方法可获取元素节点，分别通过元素ID，标签名字，类名字来获取。
##### 1.getElementById
`document.getElementById('id');`
##### 2.getElementByTagName
返回一个对象数组
`document.getElementByTagName('li');`
通配符'\*'可以作为参数，返回文档里所有节点
某份文档里总共有多少个元素节点
`document.getElementByTagName('*').length;`
##### 3.getElementByClassName
HTML5 DOM中新增的
`document.getElementByClassName('important sale')`
匹配同时含有这两个类名important sale的元素，类名顺序不影响匹配结果

>- 一份文档就是一棵节点树
- 节点分为不同的类型：元素节点，属性节点，文本节点
- getElementById将返回一个对象，该对象对应着文档里的一个特定的元素节点
- getElementByTagName和getElementByClassName将返回一个对象数组，他们分别对应着文档里的一组特定的元素节点
- 每个节点都是一个对象

### 获取和设置属性
#### getAttribute
是一个函数，他只有一个参数，就是打算查询的属性的名字。
不属于document对象，所以不能通过document对象调用。他只能通过元素节点对象调用。
#### setAttribute
只能用于元素节点。
`object.setAttribute(attribute,value)`
如果一个元素的属性不存在，setAttribute先创建这个属性，再给他赋值。
### style对象
`document.getElementById('ex').style`
#### 获取样式
css属性名中的连字符换成驼峰命名
css速记属性如font:12px 'Arial';
DOM是能够解析的，如果查询fontSize会返回12px
style对象只能返回内嵌样式，head中的`<style>`标签里的获取不到，link文件里的获取不到
`p.style.color`
`p.style.fontFamily`
#### 设置样式
赋值操作更新样式
`element.style.property=value`
style对象的属性永远是一个字符串，设置的属性值要放在引号里
`p.style.color='black'`
如果没有使用引号，会把右边的值解释为一个变量
`p.style.color=black`
用赋值操作符可以设置任何一种样式属性，诸如font之类的速记属性也不例外
`p.style.font="2em 'Times'"`

#### className属性
设置元素的类名。
className属性是一个可读写的属性，凡是元素节点都有这个属性
得到一个元素的class
`p.clasaName`

设置一个元素的class
`p.className=value`

追加一个属性，类名intro前面要有空格
`p.className+=" intro"`
## JS实现动画效果
要实现的效果：把一个元素从一个点沿直线缓慢移动到另一个点。
设置元素的起始位置，和终止位置，设置元素移动过去的时间。
1. 起始位置函数positionMessage()
设置起点位置坐标，距离上方100px，距离左方50px。
```javascript
function positionMessage(){
    var elem=document.getElementById('message');
    elem.style.position='absolute';
    elem.style.left='50px';
    elem.style.top='100px';
}
```
2. 终止位置函数moveMessage()
距离左方的位置变为200px。
```javascript
function moveMessage(){
    var elem=document.getElementById('message');
    elem.style.left='200px';
}
```
3. 移动过去的时间用函数setTimeout()来创造，这个函数能够让某个函数在经过一段预定的时间之后才开始执行。
他带有2个参数
 - 第一个参数通常是一个字符串，内容是将要执行的那个函数的名字；
 - 第二个参数是一个数值，它以毫秒为单位设定了需要经过多长时间后才开始执行第一个参数所给出的函数。

4. 如果想取消某个正在排队等待执行的函数，就必须先把setTimeout函数的返回值赋给一个变量
```javascript
v=setTimeout('function',interval);
```
然后把这个变量作为clearTimeout的参数`clearTimeout(v);`
5. 修改positionMessage函数，让他在5s之后再去调用moveMessage。
```javascript
function positionMessage(){
    var elem=document.getElementById('message');
    elem.style.position='absolute';
    elem.style.left='50px';
    elem.style.top='100px';
    
    movement=setTimeout('moveMessage()',5000);
}
```
此时动画是跳跃效果，从5s后起点一下子到了终点。
6. 更新moveMessage，让元素的移动以渐变的方式发生
 a.获得元素的当前位置；
 b.如果元素已经到达他的目的地，则退出这个函数；
 c.如果元素尚未到达他的目的地，则把他向目的地移近一些；
 d.经过一段时间间隔之后从步骤a开始重复上述步骤。
