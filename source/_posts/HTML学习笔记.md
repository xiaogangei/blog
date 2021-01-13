---
title: HTML学习笔记
name: XiaoGang
date: 2021-01-04 05:43:22
tags:
- HTML
categories: [Web]
headimg: https://s3.ax1x.com/2021/01/13/sNX8W4.png
---
学习HTML记录的一些笔记
<!--more-->
## `<base>` 标签
设置作为网页的基础连接

```html
<base href="https://www.baidu.com" target="_blank"/>
```

## `<meta>`标签
作为向浏览器传达元数据的标签
例如：
设置网页的字符编码
```html
<mate charset="utf-8"/>
```
设置网页的关键词

```html
<mate name='keywords' content="HTML5,CSS3"/>
```
设置网页的描述信息

```html
<mate name="description" content="这是一个网页的描述"/>
```
设置网页5秒自动刷新

```html
<mate http-equiv="refresh" content="5"/>
```
设置网页5秒后自动跳转到百度

```html
<mate http-equiv='refresh' content="5;url=https://www.baidu.com"/>
```
[![sCyl4K.png](https://s3.ax1x.com/2021/01/04/sCyl4K.png)](https://www.runoob.com/tags/tag-meta.html)

## `<script>`标签

script标签是用于定义网页中的各种脚本的，例如JavaScript脚本

```html
<script>
    document.write("Hello Word");
</script>
```
[![sCyj56.png](https://s3.ax1x.com/2021/01/04/sCyj56.png)](https://www.runoob.com/tags/tag-script.html)

## `<style>`标签
style标签是用于定义网页中的CSS样式的，如果使用外联CSS请使用`<link>`标签

```html
<style type="text/css">
    body{
        background:#333;
    }
</style>
```

[![sC6pxe.png](https://s3.ax1x.com/2021/01/04/sC6pxe.png)](https://www.runoob.com/tags/tag-style.html)

[Media属性的用法](https://www.runoob.com/tags/att-style-media.html)

## `<link>`标签
 link标签定义文档与外部资源的关系,最常见的用途是链接样式表。

```html
<head>
<link rel="stylesheet" type="text/css" href="theme.css">
</head>
```
[Link标签的的属性](https://www.runoob.com/tags/tag-link.html)

## `<img>`标签
img标签主要是用来在网页中插入图片的


```html
<img alt='这里是描述文字' scr='这里是图片链接'/>
<img loading="lazy" src="smiley-2.gif" alt="Smiley face" width="42" height="42">
```
[![sCcllD.png](https://s3.ax1x.com/2021/01/04/sCcllD.png)](https://www.runoob.com/tags/tag-img.html)

## HTML表格
表格由 `<table>` 标签来定义。每个表格均有若干行（由 `<tr> `标签定义），每行被分割为若干单元格（由 `<td> `标签定义）。字母 td 指表格数据（table data），即数据单元格的内容。数据单元格可以包含文本、图片、列表、段落、表单、水平线、表格等等。
```html
<table border="1">
    <tr>
        <td>row 1, cell 1</td>
        <td>row 1, cell 2</td>
    </tr>
    <tr>
        <td>row 2, cell 1</td>
        <td>row 2, cell 2</td>
    </tr>
</table>
```
<table border="1">
    <tr>
        <td>row 1, cell 1</td>
        <td>row 1, cell 2</td>
    </tr>
    <tr>
        <td>row 2, cell 1</td>
        <td>row 2, cell 2</td>
    </tr>
</table>

#### 单元格跨行

```html
  <table border="1" >
      <tr>
          <td colspan="2">标题</td>
      </tr>
      <tr>
          <td >内容</td>
          <td>内容</td>
      </tr>
  </table>
```

<table border="1" >
      <tr>
          <td  colspan="2">标题</td>
      </tr>
      <tr>
          <td >内容</td>
          <td>内容</td>
      </tr>
  </table>

#### 单元格跨列

```html
  <table border="1" >
      <tr>
          <td colspan="2">标题</td>
      </tr>
      <tr>
          <td rowspan='2'>内容</td>
          <td>内容</td>
      </tr>
      <tr>
          <td>内容</td>
      </tr>
  </table>
```
  <table border="1" >
      <tr>
          <td colspan="2">标题</td>
      </tr>
      <tr>
          <td rowspan='2'>内容</td>
          <td>内容</td>
      </tr>
      <tr>
          <td>内容</td>
      </tr>
  </table>

[![sCgE38.png](https://s3.ax1x.com/2021/01/04/sCgE38.png)](https://www.runoob.com/html/html-tables.html)

## HTML列表
### HTML无序列表
无序列表是一个项目的列表，此列项目使用粗体圆点（典型的小黑圆圈）进行标记。

无序列表使用 `<ul>` 标签
```html
<ul>
<li>Coffee</li>
<li>Milk</li>
</ul>
```
<ul>
<li>Coffee</li>
<li>Milk</li>
</ul>

### HTML 有序列表
同样，有序列表也是一列项目，列表项目使用数字进行标记。 有序列表始于 `<ol>` 标签。每个列表项始于 `<li>` 标签。
列表项使用数字来标记。

```html
<ol>
<li>Coffee</li>
<li>Milk</li>
</ol>
```
<ol>
<li>Coffee</li>
<li>Milk</li>
</ol>

### HTML 自定义列表

自定义列表不仅仅是一列项目，而是项目及其注释的组合。
自定义列表以 `<dl>` 标签开始。每个自定义列表项以 `<dt>` 开始。每个自定义列表项的定义以 `<dd>` 开始。

```html
<dl>
<dt>Coffee</dt>
<dd>- black hot drink</dd>
<dt>Milk</dt>
<dd>- white cold drink</dd>
</dl>
```
<dl>
<dt>Coffee</dt>
<dd>- black hot drink</dd>
<dt>Milk</dt>
<dd>- white cold drink</dd>
</dl>

## HTML表单
表单是一个包含表单元素的区域。

表单元素是允许用户在表单中输入内容,比如：文本域(textarea)、下拉列表、单选框(radio-buttons)、复选框(checkboxes)等等。

表单使用表单标签 `<form>` 来设置:

```html
<form>
.
input 元素
.
</form>
```
### HTML 表单 - 输入元素
多数情况下被用到的表单标签是输入标签（`<input>`）。
输入类型是由类型属性（type）定义的。大多数经常被用到的输入类型如下：

#### 文本域（Text Fields）
文本域通过`<input type="text">` 标签来设定，当用户要在表单中键入字母、数字等内容时，就会用到文本域。

```html
<form>
First name: <input type="text" name="firstname"><br>
Last name: <input type="text" name="lastname">
</form>
```

<form>
First name: <input type="text" name="firstname"><br>
Last name: <input type="text" name="lastname">
</form>
#### 密码字段
密码字段通过标签`<input type="password">` 来定义:
```html
<form>
Password: <input type="password" name="pwd">
</form>
```

<form>
Password: <input type="password" name="pwd">
</form>
#### 单选按钮（Radio Buttons）
`<input type="radio"> `标签定义了表单单选框选项

```html
<form>
<input type="radio" name="sex" value="male">Male<br>
<input type="radio" name="sex" value="female">Female
</form>
```
#### 复选框（Checkboxes）
`<input type="checkbox"> `定义了复选框. 用户需要从若干给定的选择中选取一个或若干选项。

```html
<form>
<input type="checkbox" name="vehicle" value="Bike">I have a bike<br>
<input type="checkbox" name="vehicle" value="Car">I have a car
</form>
```
<form>
<input type="checkbox" name="vehicle" value="Bike">I have a bike<br>
<input type="checkbox" name="vehicle" value="Car">I have a car
</form>

#### 提交按钮(Submit Button)
`<input type="submit"> `定义了提交按钮.

当用户单击确认按钮时，表单的内容会被传送到另一个文件。表单的动作属性定义了目的文件的文件名。由动作属性定义的这个文件通常会对接收到的输入数据进行相关的处理。:

```html
<form name="input" action="html_form_action.php" method="get">
Username: <input type="text" name="user">
<input type="submit" value="Submit">
</form>
```
<form name="input" action="html_form_action.php" method="get">
Username: <input type="text" name="user">
<input type="submit" value="Submit">
</form>
#### 文件上传

```html
<form id="upload-form" action="upload.php" method="post" enctype="multipart/form-data" >
　　　<input type="file" id="upload" name="upload" /> <br />
　　　<input type="submit" value="Upload" />
</form>
```
<form id="upload-form" action="upload.php" method="post" enctype="multipart/form-data" >
　　　<input type="file" id="upload" name="upload" /> <br />
　　　<input type="submit" value="Upload" />
</form>
[![sCgE38.png](https://s3.ax1x.com/2021/01/04/sCgE38.png)](https://www.runoob.com/html/html-forms.html)

## HTML颜色
[![sCgwU1.png](https://s3.ax1x.com/2021/01/04/sCgwU1.png)](https://www.runoob.com/html/html-colors.html)
## HTML字符实体
[![sCg04x.png](https://s3.ax1x.com/2021/01/04/sCg04x.png)](https://www.runoob.com/html/html-entities.html)
