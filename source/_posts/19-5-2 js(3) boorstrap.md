---
title: 19-5-2 js(3) boorstrap
date: 2019-5-2 18:28:59
tags: 
- 2019
- js
- boorstrap
---


![65f81697-1c2e-462f-b243-fe79d2161735.jpg](https://i.loli.net/2019/05/19/5ce1437798a1f34152.jpg)
bootstrap
<!-- more-->
### bootstrap
参考资料：[w3cschool](https://www.w3cschool.cn/bootstrap4/)
#### 基础
bootstrap是一个前端框架，能非常灵活的让界面适用于各种设备。
要使用bootstrap很简单，一种是官网下载相关代码，一种则是使用在线资源，接着引用。
```html
<head>
  <link rel="stylesheet" href="https://cdn.bootcss.com/bootstrap/4.1.0/css/bootstrap.min.css">
<!-- 可选的Bootstrap主题文件（一般不使用） -->
<script src="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap-theme.min.css"></script>
<!-- jQuery文件。务必在bootstrap.min.js 之前引入 -->
<script src="https://cdn.bootcss.com/jquery/2.1.1/jquery.min.js"></script>
<!-- 最新的 Bootstrap 核心 JavaScript 文件 -->
<script src="https://cdn.bootcss.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
</head>
```
这些文件里面预设了很多我们所能使用的东西，在我们写前端<div\>时，只需要引用就能产生相应的效果。
```html
<div class="container-fluid">
<p>使用了 .container-fluid，100% 宽度，占据全部视口（viewport）的容器。</p>
</div>
```
在所引用的文件中container-fluid被这样定义
```css
.container-fluid{width:100%;padding-right:15px;padding-left:15px;margin-right:auto;margin-left:auto}
```
![SH5CM36D75.png](https://i.loli.net/2019/05/18/5cdf63119474151101.png)
#### 布局
![MWRIXlrWLO.png!large.jpg](https://i.loli.net/2019/05/18/5cdf629aee29396689.jpg)
bootstrap将窗口分为最多12列，这种网格系统是动态响应的，根据屏幕大小重新排列。
bootstrap最外层是一个container来确定内容范围
```html
<div class="container">  //container 类用于固定宽度并支持响应式布局的容器。
  //container-fluid 类用于 100% 宽度，占据全部视口（viewport）的容器。
  //简单来看就是container有空白边 而container-fluid没有空白边
</div>
```
接着就是一个row来确定是列表内容，每个列表使用col-\*-\*来确定宽度，其中最后个数字加起来为12，不加数字就会自动平均分配。
```html
<div class="container-fluid">
  <h1>Hello World!</h1>
  <p>创建三个相等宽度的列!</p>
  <div class="row">
    <div class="col" style="background-color:lavender;">.col</div>
    <div class="col" style="background-color:orange;">.col</div>
    <div class="col" style="background-color:lavender;">.col</div>
  </div>
</div>

<div class="container-fluid">
  <h1>Hello World!</h1>
  <p>重置浏览器大小查效果。</p>
  <p> 在移动设备上，即屏幕宽度小于 576px 时，四个列将会上下堆叠排版。</p>
  <div class="row">
    <div class="col-sm-2" style="background-color:lavender;">.col-sm-3</div>
    <div class="col-sm-4" style="background-color:lavenderblush;">.col-sm-3</div>
    <div class="col-sm-1" style="background-color:lavender;">.col-sm-3</div>
    <div class="col-sm-5" style="background-color:lavenderblush;">.col-sm-3</div>
  </div>
</div>
```
当然也可以设置在不同的分辨率下显示不同的效果，只需要在class里多加上就行。
需要注意的是
- col- 针对所有设备
- col-sm- 平板 - 屏幕宽度等于或大于 576px
- col-md- 桌面显示器 - 屏幕宽度等于或大于 768px)
- col-lg- 大桌面显示器 - 屏幕宽度等于或大于 992px)
- col-xl- 超大桌面显示器 - 屏幕宽度等于或大于 1200px)

```html
<div class="container-fluid">
  <h1>平板、桌面、大桌面显示器、超大桌面显示器</h1>
  <p>以下实例在平板、桌面、大桌面显示器、超大桌面显示器的宽度比例为分别为：25%/75%、50%/50%、33.33%/66.67%、16.67/83.33%, 在移动手机等小型设备上会堆叠显示。</p>
  <p>重置浏览器窗口大小，查看效果。</p>
  <div class="container-fluid">
    <div class="row">
      <div class="col-sm-3 col-md-6 col-lg-4 col-xl-2 bg-success">
        excitingfrog
      </div>
      <div class="col-sm-9 col-md-6 col-lg-8 col-xl-10 bg-warning">
        excitingfrog
      </div>
    </div>
  </div>
</div>
```
还可以通过offset-\*-\*来设置位置偏移
```html
<div class="container-fluid">
  <h1>偏移列</h1>
  <p>.offset-md-4 是把.col-md-4 往右移了四列格。</p>
  <div class="container-fluid">
    <div class="row">
      <div class="col-md-4 bg-success">.col-md-4</div>
      <div class="col-md-4 offset-md-4 bg-warning">.col-md-4 .offset-md-4</div>
    </div>
    <div class="row">
      <div class="col-md-3 offset-md-3 bg-success">.col-md-3 .offset-md-3</div>
      <div class="col-md-3 offset-md-3 bg-warning">.col-md-3 .offset-md-3</div>
    </div>
    <div class="row">
      <div class="col-md-6 offset-md-3 bg-success">.col-md-6 .offset-md-3</div>
    </div>
  </div>
</div>
```

#### 排版
bootstrap提供了很多预设好的内容，都是可以直接在class里使用的，若果要使用多个，直接在class里空格区分，非常的方便(后加载的覆盖前面的)。
bootstrap也提供了一些标签或者是重构了一些标签，也可以直接使用。<br>
class：
- display-1,display-2..display-4 更大的标题
- text-left	左对齐
- text-center	居中
- text-right	右对齐
- ......

标签：
- <small> 更小更淡的字体
- <mark\> 黄色高亮标出
- <abbr> 显示虚线
- ......

#### 表格
![TIM截图20190519090403.jpg](https://i.loli.net/2019/05/19/5ce0ab9f87c2144890.jpg)
container下的<table\>的table类 <thead\>作为表头 <tbody\>作为内容 <tr\>为一行 <th\>为thead的一列内容 <td\>为body的一列内容 还可以继续添加class里的内容增加效果。
```html
<table class="table table-hover">
   <thead>
     <tr>
       <th>Firstname</th>
       <th>Lastname</th>
       <th>Email</th>
     </tr>
   </thead>
   <tbody>
     <tr>
       <td>John</td>
       <td>Doe</td>
       <td>john@example.com</td>
     </tr>
     <tr>
       <td>Mary</td>
       <td>Moe</td>
       <td>mary@example.com</td>
     </tr>
     <tr>
       <td>July</td>
       <td>Dooley</td>
       <td>july@example.com</td>
     </tr>
   </tbody>
 </table>
```
- table-striped 每隔一行都有浅灰背景作区分
- table-bordered 有边框
- table-hover 鼠标悬停变灰色背景
- table-dark  黑色背景
- table-primary	蓝色: 指定这是一个重要的操作
- table-success	绿色: 指定这是一个允许执行的操作
- table-danger	红色: 指定这是可以危险的操作
- table-info	浅蓝色: 表示内容已变更
- table-warning	橘色: 表示需要注意的操作
- table-active	灰色: 用于鼠标悬停效果
- table-secondary	灰色: 表示内容不怎么重要
- table-light	浅灰色，可以是表格行的背景
- table-dark	深灰色，可以是表格行的背景
- thead-dark 类用于给表头添加黑色背景
- thead-light 类用于给表头添加灰色背景
- table-sm 小表格
- table-responsive 响应式表格 宽度较小时会有滚动条
- table-responsive-sm	< 576px
- table-responsive-md	< 768px
- table-responsive-lg	< 992px
- table-responsive-xl	< 1200px

#### 图片
<img>中可以设置class为
- img-rounded：让图片显示圆角效果
- img-circle：设置椭圆形图片
- img-thumbnail：用于设置图片缩略图(图片有边框)
- float-right 类来设置图片右对齐
- float-left 类设置图片左对齐

也可以设置img-fluid来变成响应式
```html
<img src="图片地址" class="img-rounded">
<img src="图片地址" class="img-circle">
<img src="图片地址" class="img-thumbnail">
<div class="container">
  <h2>响应式图片</h2>
  <p>.img-fluid 类可以设置响应式图片，重置浏览器大小查看效果:</p>
  <img src="https://www.w3cschool.cn/attachments/image/20180524/1527144620597215.png" class="img-fluid">
</div>
```


#### 提示框
![TIM截图20190519090350.jpg](https://i.loli.net/2019/05/19/5ce0ab9f91dd677399.jpg)
class里设置alert，后面可以加上alert-success,alert-info,alert-warning, alert-danger,alert-primary,alert-secondary,alert-light或alert-dark 类来实现颜色的变化。<br>
提示框中在链接的标签上添加 alert-link 类来设置匹配提示框颜色的链接<br>
我们可以在提示框中的 div 中添加 .alert-dismissable 类，然后在关闭按钮的链接上添加 class="close" 和 data-dismiss="alert" 类来设置提示框的关闭操作。<br>
fade 和 show 类用于设置提示框在关闭时的淡出和淡入效果
```html
<div class="alert alert-warning">
   <strong>警告!</strong> 你应该认真阅读 <a href="#" class="alert-link">这条信息</a>。
 </div>

 <div class="alert alert-info alert-dismissable fade show">
   <button type="button" class="close" data-dismiss="alert">&times;</button>
   <strong>信息!</strong> 请注意这个信息。
 </div>

 <div class="alert alert-success">
   <strong>成功!</strong> 指定操作成功提示信息。
 </div>
 <div class="alert alert-info">
   <strong>信息!</strong> 请注意这个信息。
 </div>
 <div class="alert alert-warning">
   <strong>警告!</strong> 设置警告信息。
 </div>
 <div class="alert alert-danger">
   <strong>错误!</strong> 失败的操作
 </div>
 <div class="alert alert-primary">
  <strong>首选!</strong> 这是一个重要的操作信息。
 </div>
 <div class="alert alert-secondary">
  <strong>次要的!</strong> 显示一些不重要的信息。
 </div>
 <div class="alert alert-dark">
  <strong>深灰色!</strong> 深灰色提示框。
 </div>
 <div class="alert alert-light">
   <strong>浅灰色!</strong>浅灰色提示框。
 </div>
```

#### 按钮
button的class 可以设置不同的样式
![TIM截图20190519093825.jpg](https://i.loli.net/2019/05/19/5ce0b39cc9eae39633.jpg)
```html
<button type="button" class="btn">基本按钮</button>
 <button type="button" class="btn btn-primary">主要按钮</button>
 <button type="button" class="btn btn-secondary">次要按钮</button>
 <button type="button" class="btn btn-success">成功</button>
 <button type="button" class="btn btn-info">信息</button>
 <button type="button" class="btn btn-warning">警告</button>
 <button type="button" class="btn btn-danger">危险</button>
 <button type="button" class="btn btn-dark">黑色</button>
 <button type="button" class="btn btn-light">浅色</button>
 <button type="button" class="btn btn-link">链接</button>     

 <a href="#" class="btn btn-info" role="button">链接按钮</a>
  <button type="button" class="btn btn-info">按钮</button>
  <input type="button" class="btn btn-info" value="输入框按钮">
  <input type="submit" class="btn btn-info" value="提交按钮">  
```
需要一个按钮，但是不要他们自带的背景颜色可以使用.btn-outline类来实现。
```html
<button type="button" class="btn btn-outline-primary">主要按钮</button>
 <button type="button" class="btn btn-outline-secondary">次要按钮</button>
 <button type="button" class="btn btn-outline-success">成功</button>
 <button type="button" class="btn btn-outline-info">信息</button>
 <button type="button" class="btn btn-outline-warning">警告</button>
 <button type="button" class="btn btn-outline-danger">危险</button>
 <button type="button" class="btn btn-outline-dark">黑色</button>
 <button type="button" class="btn btn-outline-light text-dark">浅色</button>
 <button type="button" class="btn btn-primary btn-lg">大号按钮</button>
 <button type="button" class="btn btn-primary">默认按钮</button>
 <button type="button" class="btn btn-primary btn-sm">小号按钮</button>
```
通过添加 .btn-block 类可以设置块级按钮：可以配合row col来使用<br>
按钮可设置为激活或者禁止点击的状态。
active 类可以设置按钮是可用的，disabled 属性可以设置按钮是不可点击的。 注意 <a\> 元素不支持 disabled 属性，你可以通过添加 disabled 类来禁止链接的点击。
```html
<h2>块级按钮</h2>
 <button type="button" class="btn btn-primary btn-block">按钮 1</button>
 <button type="button" class="btn btn-default btn-block">按钮 2</button>
 <h2>大的块级按钮</h2>
 <button type="button" class="btn btn-primary btn-lg btn-block">按钮 1</button>
 <button type="button" class="btn btn-default btn-lg btn-block">按钮 2</button>
 <h2>小的块级按钮</h2>
 <button type="button" class="btn btn-primary btn-sm btn-block">按钮 1</button>
 <button type="button" class="btn btn-default btn-sm btn-block">按钮 2</button>

 <h2>按钮状态</h2>
 <button type="button" class="btn btn-primary">主要按钮</button>
 <button type="button" class="btn btn-primary active">点击后的按钮</button>
 <button type="button" class="btn btn-primary" disabled>禁止点击的按钮</button>
 <a href="#" class="btn btn-primary disabled">禁止点击的链接</a>
```

#### 按钮组
![TIM截图20190519103118.jpg](https://i.loli.net/2019/05/19/5ce0c055f1b9e66301.jpg)
<div\>里添加btn-group类来创建按钮组btn-group-sm和btn-group-lg调整大小，btn-group-vertical为垂直

```html
<h2>按钮组</h2>
<p> .btn-group 类用于创建按钮组:</p>
<h3>大按钮:</h3>
<div class="btn-group btn-group-lg">
  <button type="button" class="btn btn-primary">Apple</button>
  <button type="button" class="btn btn-primary">Samsung</button>
  <button type="button" class="btn btn-primary">Sony</button>
</div>
<h3>默认按钮:</h3>
<div class="btn-group">
  <button type="button" class="btn btn-primary">Apple</button>
  <button type="button" class="btn btn-primary">Samsung</button>
  <button type="button" class="btn btn-primary">Sony</button>
</div>
<h3>小按钮:</h3>
<div class="btn-group btn-group-sm">
  <button type="button" class="btn btn-primary">Apple</button>
  <button type="button" class="btn btn-primary">Samsung</button>
  <button type="button" class="btn btn-primary">Sony</button>
</div>
<h3>下拉按钮:</h3>
 <div class="btn-group btn-group-vertical">
  <button type="button" class="btn btn-primary">Apple</button>
  <button type="button" class="btn btn-primary">Samsung</button>
  <button type="button" class="btn btn-primary">Sony</button>
</div>
```
按钮组可以添加下拉菜单
```html
<h2>内嵌按钮组</h2>
  <p>按钮组设置下拉菜单:</p>
  <div class="btn-group">
    <button type="button" class="btn btn-primary">Apple</button>
    <button type="button" class="btn btn-primary">Samsung</button>
    <div class="btn-group">
      <button type="button" class="btn btn-primary dropdown-toggle" data-toggle="dropdown">
      Sony
      </button>
      <div class="dropdown-menu">
        <a class="dropdown-item" href="#">Tablet</a>
        <a class="dropdown-item" href="#">Smartphone</a>
      </div>
    </div>
  </div>
  <h2>拆分按钮下拉菜单</h2>
 <div class="btn-group">
   <button type="button" class="btn btn-primary">Sony</button>
   <button type="button" class="btn btn-primary dropdown-toggle dropdown-toggle-split" data-toggle="dropdown">
     <span class="caret"></span>
   </button>
   <div class="dropdown-menu">
     <a class="dropdown-item" href="#">Tablet</a>
     <a class="dropdown-item" href="#">Smartphone</a>
   </div>
 </div>
```
#### 徽章
在<span>上添加badge类，一般用于未读消息，也可以添加各种颜色,形状
![TIM截图20190519104511.jpg](https://i.loli.net/2019/05/19/5ce0c3402d31788284.jpg)
```html
<h2>各种颜色类型的徽章</h2>
<span class="badge badge-primary">主要</span>
<span class="badge badge-secondary">次要</span>
<span class="badge badge-success">成功</span>
<span class="badge badge-danger">危险</span>
<span class="badge badge-warning">警告</span>
<span class="badge badge-info">信息</span>
<span class="badge badge-light">浅色</span>
<span class="badge badge-dark">深色</span>
<h2>药丸形状徽章</h2>
<span class="badge badge-pill badge-default">默认</span>
<span class="badge badge-pill badge-primary">主要</span>
<span class="badge badge-pill badge-success">成功</span>
<span class="badge badge-pill badge-info">信息</span>
<span class="badge badge-pill badge-warning">警告</span>
<span class="badge badge-pill badge-danger">危险</span>
<button type="button" class="btn btn-primary">

   <h2>徽章嵌入到按钮内</h2>
   Messages <span class="badge badge-light">4</span>
 </button>
 <button type="button" class="btn btn-danger">
   Notifications <span class="badge badge-light">7</span>
 </button>
```
#### 进度条
在<div\>里设置类为progress,里面设置一个<div\>，class为progress-bar宽度表示进度，也可以设置高度，百分比
![TIM截图20190519151821.jpg](https://i.loli.net/2019/05/19/5ce103470bc7c44268.jpg)
```html
  <h2>进度条文本标签</h2>
  <div class="progress">
    <div class="progress-bar" style="width:70%">70%</div>
  </div>
  <div class="container">
  <h2>多种颜色的进度条</h2>
  <p>Bootstrap4 提供了以下几种进度条颜色:</p>
  <div class="progress">
    <div class="progress-bar" style="width:30%"></div>
  </div>
  <br>
  <div class="progress">
    <div class="progress-bar bg-success" style="width:40%"></div>
  </div>
  <br>
  <div class="progress">
    <div class="progress-bar bg-info" style="width:50%"></div>
  </div>
  <br>
  <div class="progress">
    <div class="progress-bar bg-warning" style="width:60%"></div>
  </div>
  <br>
  <div class="progress">
    <div class="progress-bar bg-danger" style="width:70%"></div>
  </div>
</div>
```
progress-bar-striped 类来改变进度条的样式，将其设置为条纹进度条,progress-bar-animated 类可以为进度条添加动画
```html
<h2>动画进度条</h2>
  <p>使用 .progress-bar-animated 类可以为进度条添加动画：</p>
  <div class="progress">
    <div class="progress-bar progress-bar-striped progress-bar-animated" style="width:40%"></div>
  </div>
```
几个进度条条可以叠加在一起为一条
```html
<div class="progress">
    <div class="progress-bar bg-success" style="width:40%">
      Free Space
    </div>
    <div class="progress-bar bg-warning" style="width:10%">
      Warning
    </div>
    <div class="progress-bar bg-danger" style="width:20%">
      Danger
    </div>
  </div>
```
#### 分页
![TIM截图20190519152635.jpg](https://i.loli.net/2019/05/19/5ce105366d2ad19055.jpg)

要创建一个基本的分页可以在 <ul\> 元素上添加pagination 类。然后在 <li\> 元素上添加page-item 类.当前页可以使用active 类来高亮显示。disabled 类可以设置分页链接不可点击。pagination-lg 类设置大字体的分页条目，pagination-sm 类设置小字体的分页条目
```html
<div class="container">
  <h2>分页显示大小</h2>
  <p>.pagination-lg 类设置大字体的分页条目，.pagination-sm 类设置小字体的分页条目:</p>                  
  <ul class="pagination pagination-lg">
    <li class="page-item active"><a class="page-link" href="#">Previous</a></li>
    <li class="page-item disabled"><a class="page-link" href="#">1</a></li>
    <li class="page-item"><a class="page-link" href="#">2</a></li>
    <li class="page-item"><a class="page-link" href="#">3</a></li>
    <li class="page-item"><a class="page-link" href="#">Next</a></li>
  </ul>
  <ul class="pagination pagination-sm">
    <li class="page-item"><a class="page-link" href="#">Previous</a></li>
    <li class="page-item"><a class="page-link" href="#">1</a></li>
    <li class="page-item"><a class="page-link" href="#">2</a></li>
    <li class="page-item"><a class="page-link" href="#">3</a></li>
    <li class="page-item"><a class="page-link" href="#">Next</a></li>
  </ul>
</div>
```
#### 列表组
![TIM截图20190519153404.jpg](https://i.loli.net/2019/05/19/5ce106f3dfb7d30359.jpg)

在<ul\>加list-group,<li\>加list-group-item类，active激活，disabled禁用，也可以用div替换ul，a替换li。跟之前的按钮一样设置颜色。
```html
<html>
<head>
  <title>Bootstrap4 实例</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://cdn.bootcss.com/bootstrap/4.1.0/css/bootstrap.min.css">
  <script src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
  <script src="https://cdn.bootcss.com/popper.js/1.12.5/umd/popper.min.js"></script>
  <script src="https://cdn.bootcss.com/bootstrap/4.1.0/js/bootstrap.min.js"></script>
</head>
<body>
<div class="container">
  <h2>基础列表组</h2>
  <ul class="list-group">
    <li class="list-group-item active ">First item</li>
    <li class="list-group-item disabled">Second item</li>
    <li class="list-group-item list-group-item-danger">Third item</li>
  </ul>
	 <div class="list-group">
    <a href="#" class="list-group-item list-group-item-action list-group-item-success">First item</a>
    <a href="#" class="list-group-item list-group-item-action list-group-item-info">Second item</a>
    <a href="#" class="list-group-item list-group-item-action">Third item</a>
  </div>
</div>
</body>
</html>
```

#### 卡片
![TIM截图20190519154631.jpg](https://i.loli.net/2019/05/19/5ce109de2b42372847.jpg)

card-header类用于创建卡片的头部样式，card-footer 类用于创建卡片的底部样式，card-body 类是卡片的内容。跟按钮列表一样设置颜色。卡片内容里可以加入各种内容。我们可以给 <img\> 添加 card-img-top图片在文字上方 或 card-img-bottom图片在文字下方 。如果图片要设置为背景，可以使用card-img-overlay 。
```html
<h2>多种颜色卡片</h2>
 <div class="card">
   <div class="card-body">Basic card</div>
 </div>
 <br>
 <div class="card bg-primary text-white">
   <div class="card-body">Primary card</div>
 </div>
 <br>
 <div class="card bg-success text-white">
   <div class="card-body">Success card</div>
 </div>
 <br>
 <div class="card bg-info text-white">
   <div class="card-body">Info card</div>
 </div>
  <div class="card">
    <img class="card-img-top" src="https://www.w3cschool.cn/attachments/image/20180524/1527144620597215.png" alt="Card image" style="width:100%">
    <div class="card-body">
     <h4 class="card-title">卡片标题</h4>
     <p class="card-text">卡片内容。</p>
     <a href="#" class="card-link">卡片链接</a>
     <a href="#" class="card-link">卡片链接</a>
    </div>
  </div>
```
```html
<div class="container">
  <h2>文字覆盖图片</h2>
  <p>如果图片要设置为背景，可以使用 .card-img-overlay 类:</p>
  <div class="card img-fluid" style="width:500px">
    <img class="card-img-top" src="https://www.w3cschool.cn/attachments/image/20180524/1527144620597215.png" alt="Card image" style="width:100%">
    <div class="card-img-overlay">
      <h4 class="card-title text-white">W3Cschool</h4>
      <p class="card-text text-white">Some example text some example text. Some example text some example text. Some example text some example text. Some example text some example text.</p>
      <a href="#" class="btn btn-primary">See Profile</a>
    </div>
  </div>
	</div>
```
#### 下拉菜单
![TIM截图20190519160844.jpg](https://i.loli.net/2019/05/19/5ce10f44b4f6b52109.jpg)

dropdown 类用来指定一个下拉菜单。
我们可以使用一个按钮或链接来打开下拉菜单， 按钮或链接需要添加 .dropdown-toggle 和 data-toggle="dropdown" 属性。<div\> 元素上添加 dropdown-menu 类来设置实际下拉菜单，然后在下拉菜单的选项中添加 dropdown-item 类。
dropdown-divider 类用于在下拉菜单中创建一个水平的分割线，dropdown-header 类用于在下拉菜单中添加标题，active选用，disabled禁用。
下拉菜单向上弹出，可以将 <div> 元素的 class="dropdown" 替换为 "dropup"
```html
<div class="container">
  <h2>下拉菜单</h2>
  <p>.active 类会让下拉菜单的选项高亮显示 (添加蓝色背景)。</p>
  <p>如果要禁用下拉菜单的选项，可以使用.disabled 类。</p>
  <div class="dropdown">
    <button type="button" class="btn btn-primary dropdown-toggle" data-toggle="dropdown">
      Dropdown button
    </button>
    <div class="dropdown-menu">
       <h5 class="dropdown-header">Dropdown header</h5>
      <a class="dropdown-item" href="#">Link 1</a>
      <a class="dropdown-item active" href="#">Link 2</a>
      <a class="dropdown-item" href="#">Link 3</a>
      <h5 class="dropdown-header">Dropdown header</h5>
      <a class="dropdown-item" href="#">Another link</a>
    </div>
  </div>
	<div class="dropup">
    <button type="button" class="btn btn-primary dropdown-toggle" data-toggle="dropdown">
      Dropdown button
    </button>
    <div class="dropdown-menu">
      <a class="dropdown-item" href="#">Link 1</a>
      <a class="dropdown-item" href="#">Link 2</a>
    </div>
  </div>
</div>
```
按钮中的下拉菜单在按钮中提到
#### 折叠板
将内容显示与影藏,这里data-target就是底下div的id
```html
<div class="container">
  <h2>简单的折叠</h2>
  <p>点击按钮内容会再显示与隐藏之间切换。</p>
  <button type="button" class="btn btn-primary" data-toggle="collapse" data-target="#demo">简单的折叠</button>
  <div id="demo" class="collapse">
    Lorem ipsum dolor sit amet, consectetur adipisicing elit,
    sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
    quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
  </div>
</div>
```
button一行代码也可以替换成**<a href="#demo" class="btn btn-primary" data-toggle="collapse"\>简单的折叠</a\>**
demo一行中，可以在class里加show让其默认是显示的
```html
<div class="container">
  <h2>手风琴实例</h2>
  <p><strong>注意:</strong>  使用 data-parent 属性来确保所有的折叠元素在指定的父元素下，这样就能实现在一个折叠选项显示时其他选项就隐藏。</p>
  <div id="accordion ">
    <div class="card">
      <div class="card-header">
        <a class="card-link" data-toggle="collapse" data-parent="#accordion" href="#collapseOne">
          Collapsible Group Item #1
        </a>
      </div>
      <div id="collapseOne" class="collapse show">
        <div class="card-block">
          Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
        </div>
      </div>
    </div>
    <div class="card">
      <div class="card-header">
        <a class="collapsed card-link" data-toggle="collapse" data-parent="#accordion" href="#collapseTwo">
        Collapsible Group Item #2
      </a>
      </div>
      <div id="collapseTwo" class="collapse">
        <div class="card-block">
          Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
        </div>
      </div>
    </div>
    <div class="card">
      <div class="card-header">
        <a class="collapsed card-link" data-toggle="collapse" data-parent="#accordion" href="#collapseThree">
          Collapsible Group Item #3
        </a>
      </div>
      <div id="collapseThree" class="collapse">
        <div class="card-block">
          Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.
        </div>
      </div>
    </div>
  </div>
</div>
```
#### 导航
![TIM截图20190519172454.jpg](https://i.loli.net/2019/05/19/5ce120ec1c30272994.jpg)

ul里设置nav li设置nav-item，nav可以设置居中等
```html
<ul class="nav">
   <li class="nav-item">
     <a class="nav-link" href="#">Link</a>
   </li>
   <li class="nav-item">
     <a class="nav-link" href="#">Link</a>
   </li>
   <li class="nav-item">
     <a class="nav-link" href="#">Link</a>
   </li>
   <li class="nav-item">
     <a class="nav-link disabled" href="#">Disabled</a>
   </li>
 </ul>
```
nav一行可以加上justify-content-center，justify-content-end，flex-column，如果加上nav-tabs就是标签卡，而nav-pills则是胶囊形，加上nav-justified则在容器内等宽填充。
也可以在li设置下拉单。详见下拉选单
```html
<li class="nav-item dropdown">
     <a class="nav-link dropdown-toggle" data-toggle="dropdown" href="#">Dropdown</a>
     <div class="dropdown-menu">
       <a class="dropdown-item" href="#">Link 1</a>
       <a class="dropdown-item" href="#">Link 2</a>
       <a class="dropdown-item" href="#">Link 3</a></div>
   </li>
```
配合上一节折叠板则可以实现动态选项卡效果
```html
<div class="container">
  <h2>选项卡切换</h2>
  <br>
  <!-- Nav tabs -->
  <ul class="nav nav-tabs nav-justified" role="tablist">
    <li class="nav-item">
      <a class="nav-link active" data-toggle="tab" href="#home">Home</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" data-toggle="tab" href="#menu1">Menu 1</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" data-toggle="tab" href="#menu2">Menu 2</a>
    </li>
  </ul>
  <!-- Tab panes -->
  <div class="tab-content">
    <div id="home" class="container tab-pane active"><br>
      <h3>HOME</h3>
      <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
    </div>
    <div id="menu1" class="container tab-pane fade"><br>
      <h3>Menu 1</h3>
      <p>Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
    </div>
    <div id="menu2" class="container tab-pane fade"><br>
      <h3>Menu 2</h3>
      <p>Sed ut perspiciatis unde omnis iste natus error sit voluptatem accusantium doloremque laudantium, totam rem aperiam.</p>
    </div>
  </div>
</div>
```
active是默认加载的位置所在 fade渐入，data-toggle的tab要改成pill
#### 导航栏
![TIM截图20190519191219.jpg](https://i.loli.net/2019/05/19/5ce13a1edcb9d65800.jpg)

使用 .navbar 类来创建一个标准的导航栏，后面紧跟: navbar-expand-xl|lg|md|sm 类来创建响应式的导航栏 (大屏幕水平铺开，小屏幕垂直堆叠)。导航栏上的选项可以使用 <ul\> 元素并添加 class="navbar-nav" 类。 然后在 <li\> 元素上添加 .nav-item 类,<a\> 元素上使用nav-link类。删除navbar-expand-xl|lg|md|sm就可以使得导航栏垂直。nav里的class可以设置颜色li可以设置active跟disabled
```html
<nav class="navbar navbar-expand-sm bg-dark navbar-dark">
  <ul class="navbar-nav">
    <li class="nav-item active">
      <a class="nav-link" href="#">Active</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" href="#">Link</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" href="#">Link</a>
    </li>
    <li class="nav-item">
      <a class="nav-link disabled" href="#">Disabled</a>
    </li>
  </ul>
</nav>
<nav class="navbar navbar-expand-sm bg-primary navbar-dark">
  <ul class="navbar-nav">
    <li class="nav-item active">
      <a class="nav-link" href="#">Active</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" href="#">Link</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" href="#">Link</a>
    </li>
    <li class="nav-item">
      <a class="nav-link disabled" href="#">Disabled</a>
    </li>
  </ul>
</nav>
```
还可以额外设置logo 这些都跟ul是一个层次的，在nav下
```html
<nav class="navbar navbar-expand-sm bg-dark navbar-dark">
  <!-- Brand/logo -->
  <a class="navbar-brand" href="#">Logo</a>

  <nav class="navbar navbar-expand-sm bg-dark navbar-dark">
  <!-- Brand/logo -->
  <a class="navbar-brand" href="#">
    <img src="https://www.w3cschool.cn/attachments/image/20180524/1527144620597215.png" alt="logo" style="width:40px;">
  </a>
```
也可以设置可以折叠的导航栏 或者导航栏菜单 或者输入框
```html
<nav class="navbar navbar-expand-md bg-dark navbar-dark">
  <a class="navbar-brand" href="#">Navbar</a>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#collapsibleNavbar">
    <span class="navbar-toggler-icon"></span>
  </button>
  <div class="collapse navbar-collapse" id="collapsibleNavbar">
    <ul class="navbar-nav">
      <li class="nav-item">
        <a class="nav-link" href="#">Link</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Link</a>
      </li>
      <li class="nav-item">
        <a class="nav-link" href="#">Link</a>
      </li>    
    </ul>
  </div>  
</nav>

<nav class="navbar navbar-expand-sm bg-dark navbar-dark">
  <!-- Brand -->
  <a class="navbar-brand" href="#">Logo</a>
  <!-- Links -->
  <ul class="navbar-nav">
    <li class="nav-item">
      <a class="nav-link" href="#">Link 1</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" href="#">Link 2</a>
    </li>
    <!-- Dropdown -->
    <li class="nav-item dropdown">
      <a class="nav-link dropdown-toggle" href="#" id="navbardrop" data-toggle="dropdown">
        Dropdown link
      </a>
      <div class="dropdown-menu">
        <a class="dropdown-item" href="#">Link 1</a>
        <a class="dropdown-item" href="#">Link 2</a>
        <a class="dropdown-item" href="#">Link 3</a>
      </div>
    </li>
  </ul>
</nav>

<nav class="navbar navbar-expand-sm bg-dark navbar-dark">
  <form class="form-inline">
    <input class="form-control" type="text" placeholder="Search">
    <button class="btn btn-success" type="button">Search</button>
  </form>
</nav>
```
在nav下ul同层级下可以使用类navber-text的span来输入文字。<br>
nav设置fixed-top的类可以一直停留在顶部
#### 表单
![TIM截图20190519193907.jpg](https://i.loli.net/2019/05/19/5ce14062de89754036.jpg)

```html
<h2>堆叠表单</h2>
  <form>
    <div class="form-group">
      <label for="email">Email:</label>
      <input type="email" class="form-control" id="email" placeholder="Enter email">
    </div>
    <div class="form-group">
      <label for="pwd">Password:</label>
      <input type="password" class="form-control" id="pwd" placeholder="Enter password">
    </div>
    <div class="form-check">
      <label class="form-check-label">
        <input class="form-check-input" type="checkbox"> Remember me
      </label>
    </div>
    <button type="submit" class="btn btn-primary">Submit</button>
  </form>
  <h2>内联表单</h2>
 <p>屏幕宽度在大于等于 576px 时才会水平显示。如果小于 576px 则会生成堆叠表单。</p>
 <form class="form-inline">
   <label for="email">Email:</label>
   <input type="email" class="form-control" id="email" placeholder="Enter email">
   <label for="pwd">Password:</label>
   <input type="password" class="form-control" id="pwd" placeholder="Enter password">
   <div class="form-check">
     <label class="form-check-label">
       <input class="form-check-input" type="checkbox"> Remember me
     </label>
   </div>
   <button type="submit" class="btn btn-primary">Submit</button>
 </form>
```
Bootstrap 支持所有的 HTML5 输入类型: text, password, datetime, datetime-local, date, month, time, week, number, email, url, search, tel, 以及 color
```html
<form>
  <div class="form-group">
    <label for="comment">评论:</label>
    <textarea class="form-control" rows="5" id="comment"></textarea>
  </div>
</form>
<!-- 复选-->
<form>
   <div class="form-check">
     <label class="form-check-label">
       <input type="checkbox" class="form-check-input" value="">Option 1
     </label>
   </div>
   <div class="form-check">
     <label class="form-check-label">
       <input type="checkbox" class="form-check-input" value="">Option 2
     </label>
   </div>
   <div class="form-check disabled">
     <label class="form-check-label">
       <input type="checkbox" class="form-check-input" value="" disabled>Option 3
     </label>
   </div>
 </form>
<!-- 单选-->
 <h2>表单控件: radio</h2>
 <p>以下实例包含了三个选项。最后一个是禁用的：</p>
 <form>
   <div class="radio">
     <label><input type="radio" name="optradio">Option 1</label>
   </div>
   <div class="radio">
     <label><input type="radio" name="optradio">Option 2</label>
   </div>
   <div class="radio disabled">
     <label><input type="radio" name="optradio" disabled>Option 3</label>
   </div>
 </form>
<!-- 下拉单-->
 <h2>表单控件: select</h2>
 <p>以下表单包含了两个下拉菜单 (select 列表):</p>
 <form>
   <div class="form-group">
     <label for="sel1">单选下拉菜单:</label>
     <select class="form-control" id="sel1">
       <option>1</option>
       <option>2</option>
       <option>3</option>
       <option>4</option>
     </select>
     <br>
     <label for="sel2">多选下拉菜单(按住 shift 键，可以选取多个选项):</label>
     <select multiple class="form-control" id="sel2">
       <option>1</option>
       <option>2</option>
       <option>3</option>
       <option>4</option>
       <option>5</option>
     </select>
   </div>
 </form>
```
在form-check后使用 form-check-inline 类可以让选项显示在同一行上
#### 轮播
![TIM截图20190519195521.jpg](https://i.loli.net/2019/05/19/5ce14443206f169502.jpg)

```html
<div id="demo" class="carousel slide" data-ride="carousel">
  <!-- 指示符 -->
  <ul class="carousel-indicators">
    <li data-target="#demo" data-slide-to="0" class="active"></li>
    <li data-target="#demo" data-slide-to="1"></li>
    <li data-target="#demo" data-slide-to="2"></li>
  </ul>
  <!-- 轮播图片 -->
  <div class="carousel-inner">
    <div class="carousel-item active">
      <img src="https://i.loli.net/2019/05/19/5ce1437721fc052157.jpg">
      <div class="carousel-caption">
        <h3>第一张图片描述标题</h3>
        <p>描述文字!</p>
      </div>
    </div>
    <div class="carousel-item">
      <img src="https://i.loli.net/2019/05/19/5ce143777c21a19418.jpg">
      <div class="carousel-caption">
        <h3>第二张图片描述标题</h3>
        <p>描述文字!</p>
      </div>
    </div>
    <div class="carousel-item">
      <img src="https://i.loli.net/2019/05/19/5ce1437788eea76143.jpg">
      <div class="carousel-caption">
        <h3>第三张图片描述标题</h3>
        <p>描述文字!</p>
      </div>
    </div>
  </div>
  <!-- 左右切换按钮 -->
  <a class="carousel-control-prev" href="#demo" data-slide="prev">
    <span class="carousel-control-prev-icon"></span>
  </a>
  <a class="carousel-control-next" href="#demo" data-slide="next">
    <span class="carousel-control-next-icon"></span>
  </a>
</div>
```
#### 模态框
![TIM截图20190519200042.jpg](https://i.loli.net/2019/05/19/5ce145703528493072.jpg)

```html
<h2>模态框实例</h2>
 <!-- 按钮：用于打开模态框 -->
 <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#myModal">
   打开模态框
 </button>
 <!-- 模态框 -->
 <div class="modal fade" id="myModal">
   <div class="modal-dialog modal-sm">
     <div class="modal-content">
       <!-- 模态框头部 -->
       <div class="modal-header">
         <h4 class="modal-title">模态框头部</h4>
         <button type="button" class="close" data-dismiss="modal">&times;</button>
       </div>
       <!-- 模态框主体 -->
       <div class="modal-body">
         模态框内容..
       </div>
       <!-- 模态框底部 -->
       <div class="modal-footer">
         <button type="button" class="btn btn-secondary" data-dismiss="modal">关闭</button>
       </div>
     </div>
   </div>
 </div>
```
#### 提示框
![TIM截图20190519200134.jpg](https://i.loli.net/2019/05/19/5ce145a4b443287749.jpg)

```html
<div class="container">
  <h3>提示框实例</h3><br>
  <a href="#" data-toggle="tooltip" data-placement="top" title="我是提示内容!">鼠标移动到我这</a>
  <a href="#" data-toggle="tooltip" data-placement="bottom" title="我是提示内容!">鼠标移动到我这</a>
  <a href="#" data-toggle="tooltip" data-placement="left" title="我是提示内容!">鼠标移动到我这</a>
  <a href="#" data-toggle="tooltip" data-placement="right" title="我是提示内容!">鼠标移动到我这</a>
</div>
<script>
$(document).ready(function(){
    $('[data-toggle="tooltip"]').tooltip();   
});
</script>
```

#### 弹出框
![TIM截图20190519200438.jpg](https://i.loli.net/2019/05/19/5ce1465e3875f53493.jpg)

```html
<div class="container">
  <h3>弹出框实例</h3> <br><br><br><br><br><br>
  <a href="#" title="Header" data-toggle="popover" data-placement="top" data-content="Content">点我</a>
  <a href="#" title="Header" data-toggle="popover" data-placement="bottom" data-content="Content">点我</a>
  <a href="#" title="Header" data-toggle="popover" data-trigger="focus" data-placement="left" data-content="Content">点我</a>
    <a href="#" title="Header" data-toggle="popover" data-trigger="hover" data-placement="right" data-content="Content">点我</a>
</div>
<script>
$(document).ready(function(){
    $('[data-toggle="popover"]').popover();   
});
</script>
```
默认情况下，弹出框在再次点击指定元素后就会关闭，但可以在a使用 data-trigger="focus" 属性来设置在鼠标点击元素外部区域来关闭弹出框<br>
如果你想实现在鼠标移动到元素上显示，移除后消失的效果，可以使用 data-trigger 属性，并设置值为 "hover"
#### 滑动监听
![TIM截图20190519200935.jpg](https://i.loli.net/2019/05/19/5ce147866d8ff23254.jpg)

两个实例
```html
<html>
<head>
  <title>Bootstrap4 实例</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://cdn.bootcss.com/bootstrap/4.1.0/css/bootstrap.min.css">
  <script src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
  <script src="https://cdn.bootcss.com/popper.js/1.12.5/umd/popper.min.js"></script>
  <script src="https://cdn.bootcss.com/bootstrap/4.1.0/js/bootstrap.min.js"></script>
  <style>
  body {
      position: relative;
  }
  </style>
</head>
<body data-spy="scroll" data-target=".navbar" data-offset="50">
<nav class="navbar navbar-expand-sm bg-dark navbar-dark fixed-top">  
  <ul class="navbar-nav">
    <li class="nav-item">
      <a class="nav-link" href="#section1">Section 1</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" href="#section2">Section 2</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" href="#section3">Section 3</a>
    </li>
    <li class="nav-item dropdown">
      <a class="nav-link dropdown-toggle" href="#" id="navbardrop" data-toggle="dropdown">
        Section 4
      </a>
      <div class="dropdown-menu">
        <a class="dropdown-item" href="#section41">Link 1</a>
        <a class="dropdown-item" href="#section42">Link 2</a>
      </div>
    </li>
  </ul>
</nav>
<div id="section1" class="container-fluid bg-success" style="padding-top:70px;padding-bottom:70px">
  <h1>Section 1</h1>
  <p>学编程，从W3Cschool开始！</p>
</div>
<div id="section2" class="container-fluid bg-warning" style="padding-top:70px;padding-bottom:70px">
  <h1>Section 2</h1>
  <p>学编程，从W3Cschool开始！</p>
</div>
<div id="section3" class="container-fluid bg-secondary" style="padding-top:70px;padding-bottom:70px">
  <h1>Section 3</h1>
  <p>学编程，从W3Cschool开始！</p>
</div>
<div id="section41" class="container-fluid bg-danger" style="padding-top:70px;padding-bottom:70px">
  <h1>Section 4 Submenu 1</h1>
  <p>学编程，从W3Cschool开始！</p>
</div>
<div id="section42" class="container-fluid bg-info" style="padding-top:70px;padding-bottom:70px">
  <h1>Section 4 Submenu 2</h1>
  <p>学编程，从W3Cschool开始！</p>
</div>
</body>
</html>

<html>
<head>
  <title>Bootstrap4 实例</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="stylesheet" href="https://cdn.bootcss.com/bootstrap/4.1.0/css/bootstrap.min.css">
  <script src="https://cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
  <script src="https://cdn.bootcss.com/popper.js/1.12.5/umd/popper.min.js"></script>
  <script src="https://cdn.bootcss.com/bootstrap/4.1.0/js/bootstrap.min.js"></script>
  <style>
  body {
      position: relative;
  }
  ul.nav-pills {
      top: 20px;
      position: fixed;
  }
  div.col-8 div {
      height: 500px;
  }
  </style>
</head>
<body data-spy="scroll" data-target="#myScrollspy" data-offset="1">
<div class="container-fluid">
  <div class="row">
    <nav class="col-sm-3 col-4" id="myScrollspy">
      <ul class="nav nav-pills flex-column">
        <li class="nav-item">
          <a class="nav-link active" href="#section1">Section 1</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#section2">Section 2</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#section3">Section 3</a>
        </li>
        <li class="nav-item dropdown">
          <a class="nav-link dropdown-toggle" data-toggle="dropdown" href="#">Section 4</a>
          <div class="dropdown-menu">
            <a class="dropdown-item" href="#section41">Link 1</a>
            <a class="dropdown-item" href="#section42">Link 2</a>
          </div>
        </li>
      </ul>
    </nav>
    <div class="col-sm-9 col-8">
      <div id="section1" class="bg-success">    
        <h1>Section 1</h1>
        <p>学编程，从W3Cschool开始！</p>
      </div>
      <div id="section2" class="bg-warning">
        <h1>Section 2</h1>
        <p>学编程，从W3Cschool开始！</p>
      </div>        
      <div id="section3" class="bg-secondary">         
        <h1>Section 3</h1>
        <p>学编程，从W3Cschool开始！</p>
      </div>
      <div id="section41" class="bg-danger">         
        <h1>Section 4-1</h1>
        <p>学编程，从W3Cschool开始！</p>
      </div>      
      <div id="section42" class="bg-info">         
        <h1>Section 4-2</h1>
        <p>学编程，从W3Cschool开始！</p>
      </div>
    </div>
  </div>
</div>
</body>
</html>
```
向您想要监听的元素（通常是 body）添加 data-spy="scroll" 。
然后添加 data-target 属性，它的值为导航栏的 id 或 class (.navbar)。这样就可以联系上可滚动区域。
注意可滚动项元素上的 id （<div id="section1"\>） 必须匹配导航栏上的链接选项 （<a href="#section1"\>)。
可选项data-offset 属性用于计算滚动位置时，距离顶部的偏移像素。 默认为 10 px。
