###title
```
<!DOCTYPE html>
>

<p>I get 10 times more traffic from <a href="http://google.com/"
title="Google">Google</a> than from <a href="http://search.yahoo.com/"
title="Yahoo Search">Yahoo</a> or <a href="http://search.msn.com/"
title="MSN Search">MSN</a>.</p>
</html>
```

##课程表##

<td>
	<tr>语文</tr>
	<tr>数学</tr>
</td>

<td>
	<tr>英语</tr>
	<tr>科学</tr>
</td>

<td>
	<tr>体育</tr>
	<tr>音乐</tr>
</td>    
**无序列表**
* Red
* Green
* Blue     
**有序列表**   
1.Bird    
2.McHale    
3.Parish    
#分隔符
* * *        
#引用
*   A list item with a blockquote:

    > This is a blockquote
    > inside a list item.    
   1986\. What a great season.    
#区段元素
 ##链接：
    >This is [an example](http://example.com/ "Title") inline link.

    >[This link](http://example.net/) has no title attribute.
  * * * * * * * * * * * * * *
###链接内容定义的形式为：

   >* 方括号（前面可以选择性地加上至多三个空格来缩进），里面输入链接文字
   >* 接着一个冒号
   >* 接着一个以上的空格或制表符
   >* 接着链接的网址
   >* 选择性地接着 title 
   >* 可以用单引号、双引号或是括弧包着    
##下面这三种链接的定义都是相同：##
```
[foo]: http://example.com/  "Optional Title Here"
[foo]: http://example.com/  'Optional Title Here'
[foo]: http://example.com/  (Optional Title Here)

```
Use the `printf()` function.
###图片
####很明显地，要在纯文字应用中设计一个「自然」的语法来插入图片是有一定难度的。

Markdown 使用一种和链接很相似的语法来标记图片，同样也允许两种样式： 行内式和参考式。    

行内式的图片语法看起来像是：    
![Alt text](/path/to/img.jpg)

![Alt text](/path/to/img.jpg "Optional title")
```
![Alt text](/path/to/img.jpg)

![Alt text](/path/to/img.jpg "Optional title")
```
#####详细叙述如下：    
*一个惊叹号 !
*接着一个方括号，里面放上图片的替代文字
*接着一个普通括号，里面放上图片的网址，最后还可以用引号包住并加上 选择性的 'title' 文字。
参考式的图片语法则长得像这样：