# HTML入门笔记2

[toc]



## 1.a标签

`<a>`标签的基本语法如下：

```html
<a href=""></a>
```

href是a标签的最基本的属性。除此之外，a标签还有target、download、rel=noopener等属性。

a标签的总体作用大概有以下几点：

- 跳转到外部页面（最常用，最多人了解，就是用户俗称的超链接）
- 跳转到内部锚点（如在第7行写一句a标签，其中href="#xxx"，xxx为第100行的div的id名，则在网页里点击此a标签可直接跳转到同一页面的div处）
- 跳转到邮箱电话

### 1.1 href属性

href=hyper reference，是a标签最基本的属性。其可能的取值如下：

1. **网址**

   作用：从自己写的此网页链接到一个外部网页。

   ```html
   	<a href="https://google.com"></a>
       <a href="http://google.com"></a>
       <a href="//google.com"></a>
   ```

   > 尽量使用第三种写法。因为第三种写法最高级，它会自动选择使用http还是https。前两种如果选错了会出现bug。

2. **路径**

   作用：从自己写的此网页（假设叫demo.html）链接到一个指定路径的文件（此例中链接到一个html文件即另一个自己编写的网站）：

   ```html
   <a href="/a/b/c/index.html"></a>
   ```

   > （上例中的a文件夹与demo.html位于同一文件夹下，所以/a/b/c/index.html其实是相对路径。原因：/开头的写法在文件系统表示法中表示绝对路径，/a在文件系统中意味着根目录下的a盘。但此处不再是文件系统，而是http系统，http默认/是开启http-server的根目录，也就是说，咱们是在demo.html所在目录（假设叫xyx）开启的http-server服务，那现在根目录就是xyx，而不是操作系统的根目录/）

3. **伪协议**

   可以直接执行js代码（早期使用，现在几乎不用这种写法了）；可以发邮件；可以拨打电话。

   现在伪协议常用来实现一个场景（见第2行）：用户点击a标签却什么也不执行。

   ```html
       <a href="javascript:alert(1);">javascript伪协议，点击此处执行alert(1)</a>
       <a href="javascript:;">点我啥也不执行，试试吧</a>
   
       <a href="mailto:xxxxxxxxx@163.com">点击此处给我发邮件</a>
       <a href="tel:182xxxxxxxx">点击此处给我拨打电话</a>
   ```

4. **id**

   即跳转到内部锚点。

   ```html
       <a href="#xxx">点击此处返回xxx部分</a>
   ```

### 1.2 target属性

内置名字：

- _blank:点击a标签后在新窗口打开（中国网站常用这种打开方式）；
- _top:点击a标签后在最顶层页面打开；
- _parent:点击a标签后在上一层页面打开；
- _self(默认值):点击a标签后在当前页面打开（国外网站常用这种打开方式）；

举个例子，比如母页面叫index1.html，其内部用iframe标签引入了一个index2.html，index2.html里以同样的方式引入了index3.html，则在index3.html里的a标签被点击后，如果target=_top,则新页面是在index1.html中被打开，如果target=parent，则新页面是在index2.html中被打开）

程序员命名：

- window的name：target=xxx:在一个叫xxx的窗口打开，如若没有便创立一个新窗口，命名为xxx。
- iframe的name：target=xxx，target=yyy。如果在网页里嵌入两个iframe分别叫xxx和yyy，则在点击a标签后直接在相应名字的iframe中打开新窗口。

### 1.3 download属性（略）

- 作用：下载页面
- 问题：不是所用浏览器都支持，尤其是手机浏览器可能不支持

## 2.iframe标签（略）

内嵌窗口标签，现在已经不常用了。现在的前端通常采用Ajax的方式完成，之后再学。

## 3.table标签

先来看该标签的基础架构：

```html
<table>
    <thead></thead>
    <tbody></tbody>
    <tfoot></tfoot>
</table>
```

再来看该标签的细节架构：

```html
    <thead>
        <tr>
            <th>语文</th> <th>英语</th> <th>数学</th>
        </tr>
    </thead>

    <tbody>
        <tr>
            <td>100</td> <td>99</td> <td>95</td>
        </tr>
    </tbody>
```

可以看到，table标签被总分为三部分：thead，tbody，和tfoot，分别表示表头，表内容，表尾。

在具体编写表格内容时，不管是表头还是表内容，每一行都要用tr包起来（tr是table row的缩写），每个表头的单元格用th包起来，每个表内容的单元格的内容用td包起来（td是table data的缩写）。

相关样式：

- table-layout：取值有fixed、auto等等，用于控制表格的形状大小模式。

- border-collapse：常用取值为collapse，表示将表格的缝隙合并。

- border-spacing：常用取值为0，表示单元格之间不留空隙。

  因此写css代码的时候常在一开始就加如下语句：

```css
        table {
            border-collapse: collapse;
            border-spacing: 0;
        }
```

## 4.image标签

常用用法：

```HTML
<img src="" alt="">
```

src是图片URL地址，可以是本地的可以是网络（存在远端服务器）的；alt是如果图片加载失败后显示的内容。

其余常用属性有height和width，注意：一般只写一个，不然大概率会使得图片变形。

为了网页是响应式页面，还应加入下面语句：

```css
img{
            max-width: 100%;
        }
```

img标签是**可替换元素**，面试常问。

## 5.form标签

作用：发出GET或POST请求，然后刷新页面。

常见属性：

- **action**：你要请求页面的地址URL（通常在后端）；
- autocomplete：取值为on的时候表示为浏览器提供关于字段中所期望的信息类型的指导；
- method：取值有GET和POST，表示浏览器采用何种http方式来提交表单；
- target：表示浏览器提交表单后在哪里显示响应信息，其取值与相应的含义跟a标签一样。

## 6.input标签

作用：让用户输入内容

常见属性：

- button
- checkbox
- file
- submit



其余有什么问题还会后续补充。