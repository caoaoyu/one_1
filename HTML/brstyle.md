####如何给br加宽高背景等颜色    
######代码如下    
```
<style type="text/css">


br{
content: " ";
display: block;
margin: 10px 0;
width:40px;
height:50px;
line-height:22px;
background-color:red;

}


</style>
</head>

<body>
换行<br/>换行换行换行换行<br/>换行换行换行换行
</body>
```
利用content的内容属性  将br变成一个框，如此便可设置颜色宽高等样式