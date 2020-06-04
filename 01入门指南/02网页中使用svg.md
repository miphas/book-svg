### 将 SVG 引入的方式

#### 1. 将 SVG 作为图像  

1.1 在<img>元素内包含SVG

``` xml
<img src="cat.svg" title="Cat Image" alt="Stick Figure of a Cat" />
```

1.2 在CSS中包含SVG

``` css
div.background-cat {
  background-image: url("cat.png");
  background-size: 100% 100%;
}
```
PS. 还可以作为 
- list-image 装饰性项目列表
- border-image 创建花哨的边框

#### 2. 将 SVG 作为应用程序

``` xml
<object data="cat.svg" type="image/svg+xml" title="Cat Object" alt="Stick Figure of a Cat">
  <!-- 文本或者栅格图作为备选 -->
  <p>No SVG support!</p>
  <img src="cat.png"></img>
</object>
```

- object 之前有 embed 元素可以达到相同的目的
- 二者有两个区别：
  - embed 使用 src 而非 data 属性
  - embed 不包含备选项，嵌入失败就没有备用选项


#### 3. 混合文档中的 SVG 标记

- 标记混合到一个文档中，浏览器就无需单独下载 SVG
- 如果同一个站点的多个应用页面使用同一个图像则会重复出现 SVG 标记并增加总体积和下载时间

1. switch 配合 foreignObject 元素实现

- foreignObject 指定了一个矩形区域，Web 浏览器应该在其中绘制 XML 内容，浏览器负责如何进行绘制

2. 在 XHTML 或者 HTML5 中内联 SVG

``` xml
<body>
  <svg>
    ...
  </svg>
</body>
```

- 可以为 SVG 指定其样式
- 文档主体样式也会被 SVG 继承
- 可以在主样式内为 SVG 定义样式

#### 4. 其他 XML 应用程序中的 SVG
一种经常内联 SVG 的方式 XSL-FO 文件

``` xml
<fo:instream-foreign-object width="140px" height="140px">
  <svg>
    ...
  </svg>
</fo:instream-foreign-object>
```