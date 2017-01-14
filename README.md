# html-kindle-book-demo

使用 HTML以及CSS技术，制作kindle电子书的模版。


# 电子书结构

## mycover.jpg

This is the cover of your book.

## mykindlebook.html

This is the content of your book – what your readers will read. Keep the HTML simple and refer to Amazon’s documentation for details on how they want you to write your markup.

## toc.html

This is the table of contents. You’ll see that each link points to a part of the Kindle book using anchor points.

## style.css

This is your stylesheet and it’s how you’ll design your book using CSS 3. I’ve styled my book so text is green (cripes) and images float to the right. Amazon’s support for CSS 3 is new as of January 2012 and pretty darn exciting because of the new design options it brings. You can learn more about the CSS 3 tags Amazon supports on its various devices here.

## mykindlebook.opf

This is an XML file that tells the Kindle how your book is structured. Go ahead and open it up (you can use TextEdit if you don’t have a code editor).

The stuff between the <metadata> tags defines the metadata for the book using standard Dublin Core elements: title, creator, date, etc.

The stuff between the <manifest> tags tells Kindle where things are. For example, you’ll see that it has references to all the files we’re currently reviewing: the cover image, the book HTML file, the table of contents HTML file, the stylesheet, and the NCX file (I’ll explain that in a moment).

The stuff between the <spine> tags tells Kindle the order of how those HTML files should be read. Using this file, for example, when you open your book on a Kindle you’ll first hit the table of contents. Then you’ll hit the book contents. See how the “idref” in the <spine> elements match the “id” in the <manifest> elements? That’s how the spine knows what HTML files to present. That matching is required, of course, otherwise Kindle won’t know what to load. You can create multiple HTML files and define the order they will be accessed in the <spine>. Be sure to also make reference to those HTML files in your <manifest> so that Kindle knows where they are located!

## toc.ncx

You know that bar along the bottom of a Kindle that has points that allow you to skip to various parts? The NCX file tells Kindle where those points are. The <navPoint> elements within the <navMap> tags define those points. For more details, check out this post: http://www.cjs-easy-as-pie.com/p/create-ncx-file-by-araby-greene.html.

## img folder
I also put a folder called “img” in the download and I threw in a nice de Kooning picture that you’ll see embedded in mykindlebook.html file.


# kindelgen

## 安装
```
brew install Caskroom/cask/kindlegen
```

## 使用

```
zip -r kindleBook.zip ./myKindleBook/*
mv kindleBook.zip kindleBook.epub
kindlegen kindleBook.epub
```

创建成功信息：
```
*************************************************************
 Amazon kindlegen(MAC OSX) V2.9 build 1028-0897292 
 命令行电子书制作软件 
 Copyright Amazon.com and its Affiliates 2014 
*************************************************************

信息(prcgen):I1047: 已添加的元数据dc:Title        "My Kindle Book"
信息(prcgen):I1047: 已添加的元数据dc:Date         "2011-12-07"
信息(prcgen):I1047: 已添加的元数据ISBN            "123456789X"
信息(prcgen):I1047: 已添加的元数据dc:Creator      "Perry Garvin"
信息(prcgen):I1047: 已添加的元数据dc:Publisher    "Amazon.com"
信息(prcgen):I1047: 已添加的元数据dc:Subject      "Reference"
信息(prcgen):I1047: 已添加的元数据dc:Description  "A short paragraph describing the publication …"
信息(prcgen):I1002: 解析文件  0000002
信息(prcgen):I1015: 创建 PRC 文件
信息(prcgen):I1006: 分析超链接
信息(prcgen):I1008: 分析读取起始位置
信息(prcgen):I1049: 创建目录     网址： /var/folders/4l/v21_twrs785_d4z1spc_11kr0000gn/T/mobi-UWjwWU/myKindleBook/toc.ncx
信息(pagemap):I8000: 没有在本书中发现页面图像
信息(prcgen):I1045: 本书中使用 UNICODE 范围计算
信息(prcgen):I1046: 已发现的 UNICODE 范围：Basic Latin [20..7E]
信息(prcgen):I1017: 创建 PRC 文件，记录数：  0000002
信息(prcgen):I1039: 最终统计 - 文本压缩为（原始大小的 %）：  34.30%
信息(prcgen):I1040: 文档标识符是： "My_Kindle_Book"
信息(prcgen):I1041: 文件格式版本是 V6
信息(prcgen):I1031: 保存 PRC 文件
信息(prcgen):I1032: 成功创建 PRC
信息(prcgen):I1016: 创建改进的 PRC 文件
信息(prcgen):I1007: 分析媒体链接
信息(prcgen):I1011: 写入媒体链接
信息(prcgen):I1009: 分析指导项
信息(prcgen):I1039: 最终统计 - 文本压缩为（原始大小的 %）：  34.79%
信息(prcgen):I1041: 文件格式版本是 V8
信息(prcgen):I15000:可交付标准Mobi文件大小约为：  0000064KB
信息(prcgen):I15001:  KF8 可交付文件大小约为：  0000066KB
信息(prcgen):I1036: 成功创建 Mobi 域名文件
```

# 参考
* [How to Make an Amazon Kindle Book using HTML and CSS](http://www.perrygarvin.com/blog/2012/01/16/how-to-make-an-amazon-kindle-book-using-html-and-css/)
* [Amazon Kindle Publishing Guidelines](http://kindlegen.s3.amazonaws.com/AmazonKindlePublishingGuidelines.pdf)
* [EPUB Publications 3.0](http://www.idpf.org/epub/30/spec/epub30-publications.html)
* [How to Make a Kindle eBook from Scratch](https://www.aliciaramirez.com/2014/05/how-to-make-a-kindle-ebook-from-scratch/)

