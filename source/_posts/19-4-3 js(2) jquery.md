---
title: 19-4-3 js(2) jquery
date: 2019-4-3 18:28:59
tags: 
- 2019
- js
- jquery
---


![](https://i.loli.net/2019/04/12/5cb03db94a5f5.jpg)
- DOM
- jQuery
<!-- more -->
### DOM相关
#### 基本
在浏览器的开发者界面F12，可以非常清楚的选择一个元素，查看其DOM结构等内容
#### 选择
最常用的就是使用document.getElementById()选择id接节点，
document.getElementsByTagName()
以及CSS选择器document.getElementsByClassName()
下面两种返回一组节点 为了限定范围，一般先限定id节点
```js
  var trs = document.getElementById('test').getElementsByTagName('tr')//选择所有tr
  var trs = document.getElementById('test').getElementsByClassName('red')//选择class = 'red'的所有节点
```
#### 修改
选择后就可以进行添加跟修改相关内容
```js
  var p = document.getElementById('pid');
  p.innerHTLM = '123';//直接修改内容
  p.style.color = '#ff0000';


  haskell = document.createElement('p');
  haskell.id = 'hsk';
  haskell.innerText = 'Haskell';
  list = document.getElementById('list');
  list.appendChild(haskell);//添加新的内容
```
insertBefore(haskell,ref)可以把元素插入ref节点之前
#### 删除
```html
<ul id="test-list">
  <li>JavaScript</li>
  <li>Swift</li>
  <li>HTML</li>
  <li>ANSI C</li>
  <li>CSS</li>
  <li>DirectX</li>
</ul>
```
```js
  var testlist = getElementById('test-list');
  testlist.removeChild(testlist.children[0]);
```
#### 表单
getElementById也可以获取input，然后可以通过value获取值
```js
  var email = document.getElementById('email');
  email.value;//获取
  email.value = 'xxxxx';//修改

  <input type="text" id="email">
```
### promise
promise可以很清晰的将几个任务串联起来
job1.then(job2).then(job3).catch(handleError);


### jQuery
#### 基本
上面的方法操作DOM有点繁杂 不如用jquery，jQuery好处有很多，轻松操作DOM，实现动画等等，而且使用很简单,直接在head中引用就行。
```HTML
<head>
  <script src="//code.jquery.com/jquery-1.11.3.min.js"></script>
  ...
</head>
```
jQuery把所有内容封装在$符号中，window.jQuery === window.$
#### 选择
jQuery选择就非常容易
```js
  //根据id
  var test = $('#abc');
  var test1 = test.get(0);//取其中第一个DOM元素
  //根据tag
  var ps = $('p');
  //根据class
  var cs = $('.red');
  //按属性查找
  var password = $('[type=password]');
  var password = $('[type^=pass]');//找出以pass开头的
  var password = $('[type$=word]');//找出以word结尾的
  var cl = $('[class^="cl"]');//找出所有class至少含有一个cl开头的
  //组合查找
  var einput = $('input[name=email]');//input下name为email
  var trred = $('tr.red');//tr下class=red
  //多项选择
  var pdiv = $('p,div');
  var redgreen = $('p.red,p.green');

  <!-- HTML结构 -->
<div class="testing">
    <ul class="lang">
        <li class="lang-javascript">JavaScript</li>
        <li class="lang-python">Python</li>
        <li class="lang-lua">Lua</li>
    </ul>
</div>

  //层级选择
  $('ul.lang li.lang-lua');//<li class="lang-lua">Lua</li>
  $('ul.lang>li.lang-lua');//子选择器 只能一层一层选择
  var py = $('.lang-python');//Python
  py.next();//Lua
  py.prev();//JavaScript
```

#### 过滤
可以通过filter过滤已经选择的节点中的节点
```js
  var lan = $('ul.lang li');
  var lua = lan.filter('.lang-lua');//过滤掉Lua
```

#### 操作
text()和html()无参数时获取内容，有参数时进行修改。
```js
  var py = $('.lang-python');
  py.text('123');//修改为123
  py.html('<span style="color: red">123</span>');//颜色修改为红色
  $('.noex').text('1123');//没有noex节点，但是也不会报错
```
还可以修改css，修改作用于style，具有最高优先级
```js
  $('ul.lang li.lang-lua>span').css('background-color','#ffd351').css('color','red');
  $('ul.lang li.lang-lua>span').css('background-color','').css('color','');//清除css属性
```
还可以修改class
```js
  var div = $('#textdiv');//
  div.hasClass('highlight');//是否含有highlight这个class
  div.addClass('highlight');//添加class
  div.removeClass('highlight');//移除class
```
使用show(),hide()进行隐藏，显示
```js
  var div = $('#textdiv');//
  div.hide();
  div.show();
```
还可以直接获取相应的信息
```js
  $(window).width();//获取窗口宽度
  $(document).width();//获取文档宽度
  $('.textdiv').height();//div的高度
  $('.textdiv').attr('name');//获取name
  $('.textdiv').attr('name','hello');//将name改为hello
  $('.textdiv').removeAttr('name');//移除name属性
  $('.ck').is(':checked');//true 或者 false  ':selected'
  $('.inp').val();  $('.inp').val('123');//获取表单元素 或者 修改
```
append()可以添加新的节点
```js
<div id="test-div">
  <ul>
      <li><span>JavaScript</span></li>
      <li><span>Python</span></li>
      <li><span>Swift</span></li>
  </ul>
</div>

//
var ul = $('#test-div>ul');
ul.append('<li><span>C</span></li>')
```
#### 事件
jQuery有很多事件包括鼠标事件click，dblclick......键盘事件keydown,keyuo......其他事件focus,change,submit......
**ready事件是在DOM完成后触发，仅作用于document,适合用来写其他的初始化代码**
```js
  $(document).ready(function(){
    //因为js执行时有些元素还没加载完，所以包含于此函数内
    //甚至可以简化成$(function(){})
    $('#test_button').click(function(){
      alert('123');
    });
  });

  $('#test_button').off('click');//解除绑定
```
有些事件的触发是只能用户才能触发，比如文本框的改动，js改动则不会触发
```js
  $('text-input').change(function(){
    alert('123');
  });
  //$('text-input').val('123123'); 不会触发
  $('text-input').change();//可以触发
```

#### 动画
jq实现动画很方便，只需要简单的在hide和show里面加入参数，或者使用toggle等进行div的消失与出现
```js
  //从左上角
  var tdiv = $('#test-div');
  tdiv.hide(1000);//一秒内消失
  tdiv.show('slow');//0.6秒内消失
  tdiv.toggle('slow');
  //从下收起
  tdiv.slideUp('slow');
  tdiv.sildeDown('slow');
  tdiv.slideToggle('slow');
  //渐出渐入
  tdiv.fadeOut('slow');
  tdiv.fadeIn('slow');
  tdiv.fadeToggle('slow');
```
jq也可以自定义动画，只需要指定最终样式，jq就能实现转变的动画效果
```js
  tdiv.animate({
    width:'200px',
    height:'200px',
  },1000);
  //最后可以再添加一个函数，执行完成后会继续执行函数
  tdiv.animate({
    width:'200px',
    height:'200px',
  },1000，function(){
    $(this).css('height','100px').css('width','100px');
  });
```
动画效果可以串行
```js
  tdiv.slideDown(1000)
  .delay(1000)
  .animate({
    width:'200px',
    height:'200px',
  },1000);
```
#### AJAX
ajax异步 JavaScript 和 XML（Asynchronous JavaScript and XML），可以用来获取信息，包括非本地的信息。
```js
  $('#test-div').load(url,data,callback);//data是请求发送的数据，callback方法完成后的所执行的函数
  //
  <div id="div1"><h2>使用 jQuery AJAX</h2></div>
    <button>获取外部内容</button>

  $(document).ready(function(){
    $('button').click(function(){
      $('#div1').load("/xxxx.txt #p1");//选取txt文件里面的p1
    });
  });
```
get()和post() get通过http get获得数据 post则使用post
```js
  $.get(url,callback);
  $.post(url,data,callback);
```
#### 编写插件
通过$.fn对象来实现,之后就可以直接使用
```js
  $.fn.highlightS = function(){
    this.css('backgroundColor','#fffceb').css('color','#d85030');
    return this;//加了this确保能够链式 例如$('#test-div').highlightS().sildeDown();
  }
  $('#test-div').highlightS();
  //也可以让用户传入参数
  $.fn.highlightUser = function(options){
    var bgcolor = options && options.backgroundColor || '#fffceb';
    var cor = options && options.color || '#d85030';
    this.css('backgroundColor', bgcolor).css('color', cor);
  }
  $('#test-div').highlightUser({
    backgroundColor : '#00a8e6',
    color : '#ffffff'
  });
  //也可以让用户自己设置默认值
  //$.extend(target, obj1, obj2) 把多个object对象合并到一个属性里
  $.fn.highlightFinal = function(options){
    var opts = $.extend({}, $.fn.highlightFinal.defaults, options);
    this.css('backgroundColor', opts.backgroundColor).css('color', opts.color);
    return this;
  }

  $.fn.highlightFinal.defaults = {
    color: '#d85030',
    backgroundColor: '#fff8de'
  }

```
