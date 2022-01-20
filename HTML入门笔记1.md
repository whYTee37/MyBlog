# HTML入门笔记1

> 本篇记录略去了写代码前需要做的准备工作，比如用什么编辑器，如何调试等等。着重放在HTML的内容上。

[toc]

## 1.HTML历史（简）

​		说到HTML就不得不cue到万维网，也就是我们俗称的WWW。WWW是由英国的计算机科学家Tim Berners-**Lee**发明的，我们一般称他为李爵士。万维网基于互联网而设计，最初的核心目的是：让用户键入一个网址（URL）就能访问到这个网址的页面。为了使WWW能正常工作，李爵士发明了HTTP，URL和HTML。可以简单理解为：
$$
WWW=URL+HTML+HTTP
$$

## 2.HTML起手式

​		HTML是一门**标记语言**，HTML起手式指的就是一个.html文件中最外面的那个框架，也是html书写时的开头。（类比C/C++,在写之前都要引用头文件，比如`#include\<iosteam>`,`#include\<stdio.h>`,虽然头文件和html的起手式不是一个实现原理，但是从程序员的习惯上来讲就是每次敲代码都要**先输入**的那个部分）

​		一般的起手式如下：（在vscode里键入感叹号【**!**】然后按tab或者回车即可自动补全）

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

> \<head>中通常是一些在网页上不呈现的、不能直观看到的元素。还要注意，自动补全的起手式，默认`lang="en"`。程序员做简体中文页面的话要改为`lang="zh-CN"`.

另外：

- **UTF-8**是字符集的一种，通常我们选取**UTF-8**，因为它兼容世界上绝大多数语言。
- `<meta http-equiv="X-UA-Compatible" content="IE=edge">`是让浏览器采用最新的IE标准渲染（目前是IE11）。
- `<meta name="viewport" content="width=device-width, initial-scale=1.0">`是为了防止页面缩放。
- `<title>`是网页的名字。

## 3.常用的章节标签

- h1~h6:**HTML `<h1>`–`<h6>` 标题(Heading)元素**呈现了六个不同的级别的标题，`<h1>` 级别最高，而 `<h6>` 级别最低。
- section:**HTML `<section>`元素**表示一个包含在HTML文档中的独立部分，它没有更具体的语义元素来表示，一般来说会有包含一个标题。
- article:**HTML `<article>`**元素表示文档、页面、应用或网站中的独立结构，其意在成为可独立分配的或可复用的结构，如在发布中，它可能是论坛帖子、杂志或新闻文章、博客、用户提交的评论、交互式组件，或者其他独立的内容项目。
- main:**HTML** **`<main>` **呈现了文档的**`body`**或应用的主体部分。主体部分由与文档直接相关，或者扩展于文档的中心主题、应用的主要功能部分的内容组成。
- aside:**HTML `<aside>` **表示一个和其余页面内容几乎无关的部分，被认为是独立于该内容的一部分并且可以被单独的拆分出来而不会使整体受影响。其通常表现为侧边栏或者标注框（call-out boxes）。
- header：**HTML `<header>` 元素**用于展示介绍性内容，通常包含一组介绍性的或是辅助导航的实用元素。它可能包含一些标题元素，但也可能包含其他元素，比如 Logo、搜索框、作者名称，等等。
- footer：**HTML <footer> 元素**表示最近一个章节内容或者根节点（sectioning root ）元素的页脚。一个页脚通常包含该章节作者、版权数据或者与文档相关的链接等信息。
- p：**HTML `<p>`**元素（或者说 HTML 段落元素）表示文本的一个段落。该元素通常表现为一整块与相邻文本分离的文本，或以垂直的空白隔离或以首行缩进。另外，`<p>` 是块级元素。
- div：内容划分元素，常跟CSS搭配使用。

## 4.全局属性

全局属性，即所有的标签都可以拥有的属性，如：

- class：**`class`** 的值是一个以空格分隔的元素的类名（classes ）列表，它允许 CSS 和 Javascript 通过类选择器 ([class selectors](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Class_selectors)) 或DOM方法( [`document.getElementsByClassName`](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/getElementsByClassName))来选择和访问特定的元素。
- id：**`id` **定义了一个全文档唯一的标识符 (ID)。它用于在链接（使用[片段](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Basics_of_HTTP/Identifying_resources_on_the_Web#片段)）、脚本和样式（通过 [CSS](https://developer.mozilla.org/zh-CN/docs/Glossary/CSS)）中辨识元素。
- style：**`<style>`**包含文档的样式信息或者文档的部分内容。默认情况下，该标签的样式信息通常是[CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)的格式。
- contenteditable： **contenteditable** 是一个枚举属性，表示元素是否可被用户编辑。 如果可以，浏览器会修改元素的部件以允许编辑。
- hidden：**`hidden`** 是一个布尔属性，表示一个元素尚未或者不再相关。例如，它可以被用来隐藏一个页面元素直到登录完毕。如果一个元素设置了这个属性，它就不会被显示。
- tabindex：指示其元素是否可以聚焦，以及它是否/在何处参与顺序键盘导航（通常使用Tab键，因此得名）。
- title：包含了表示咨询信息文本，和它属于的元素相关。这个信息通常存在，但绝不必要，作为提示信息展示给用户。

## 5.常见的内容标签

- a:HTML <a> 元素（或称锚元素）可以通过它的href创建通向其他网页、文件、同一页面内的位置、电子邮件地址或任何其他 URL 的超链接。<a> 中的内容应该指明链接的意图。如果存在 href 属性，当 <a> 元素聚焦时按下回车键就会激活它。
- strong: `<strong>`表示文本十分重要，一般用粗体显示。
- em:**HTML 着重元素 `<em>`**标记出需要用户着重阅读的内容， `<em>` 元素是可以嵌套的，嵌套层次越深，则其包含的内容被认定为越需要着重阅读。
- code:**HTML `<code>` 元素**呈现一段计算机代码. 默认情况下, 它以浏览器的默认等宽字体显示.
- pre:**HTML `<pre>`** 元素表示预定义格式文本。在该元素中的文本通常按照原文件中的编排，以等宽字体的形式展现出来，**文本中的空白符（比如空格和换行符）都会显示出来**。
- ol+li(ordered list+list item):有序列表
- ul+li(unordered list+list item):无序列表
- dl+dt+dd(description list+description term+desctiption data):描述列表
