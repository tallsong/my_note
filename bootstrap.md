

# Bootstrap 
[菜鸟链接](https://www.runoob.com/bootstrap/bootstrap-tutorial.html)
[官网的链接](https://v2.bootcss.com/base-css.html#tables)
## 网格系统（Grid System）
 基本结构
```html
<div class="container">
   <div class="row">
      <div class="col-*-*"></div>  <!-- 内容应该放置在列内，且唯有列可以是行的直接子元素。 -->
      <div class="col-*-*"></div>      
   </div>
   <div class="row">...</div>
</div>
<div class="container">....
```
.col-xs-4表示列的宽度为4.总宽度为12，故一行排三个;

|        |	超小设备手机（<768px）| 小型设备平板电脑（≥768px）  | 中型设备台式电脑（≥992px）  | 大型设备台式电脑（≥1200px） |
|  ----  | ----  |----  |----  |----  |
|Class 前缀  | .col-xs- |.col-sm- | .col-md- | .col-lg-|



您可以很轻易地改变带有 .col-md-push-* 和 .col-md-pull-* 类的内置网格列的顺序，其中 * 范围是从 1 到 11,可以很容易地以一种顺序编写列，然后以另一种顺序显示列。

## 排版
### 内联子标题
如果需要向任何标题添加一个内联子标题，只需要简单地在元素两旁添加 <small>，或者添加 .small class，这样子您就能得到一个字号更小的颜色更浅的文本
### 引导主体副本
给段落添加强调文本，则可以添加 class="lead"，这将得到更大更粗、行高更高的文本
### 缩写
Bootstrap 定义 <abbr> 元素的样式为显示在文本底部的一条虚线边框，当鼠标悬停在上面时会显示完整的文本（只要您为 <abbr> title 属性添加了文本）。为了得到一个更小字体的文本，请添加 .initialism 到 <abbr>。
### 地址
使用 <address> 标签，您可以在网页上显示联系信息。
## 列表
有序列表，无序列表，定义列表
## 代码
Bootstrap 允许您以两种方式显示代码：
```html
	<p><code>&lt;header&gt;</code> 作为内联元素被包围。</p>
<p>如果需要把代码显示为一个独立的块元素，请使用 &lt;pre&gt; 标签：</p>
<pre>
    &lt;article&gt;
        &lt;h1&gt;Article Heading&lt;/h1&gt;
    &lt;/article&gt;
</pre>
```
## 表单
在本章中，我们将学习 Bootstrap 对图片的支持。Bootstrap 提供了三个可对图片应用简单样式的 class：
```
.img-rounded：添加 border-radius:6px 来获得图片圆角。
.img-circle：添加 border-radius:50% 来让整个图片变成圆形。
.img-thumbnail：添加一些内边距（padding）和一个灰色的边框。
```
通过在 <img> 标签添加 .img-responsive 类来让图片支持响应式设计。 图片将很好地扩展到父元素。

.img-responsive 类将 max-width: 100%; 和 height: auto; 样式应用在图片上：

## 什么是字体图标

## 下拉菜单

## Bootstrap 进度条