###javascript的console.log()用法小结
##### 对于JavaScript程序的调试，相比于alert()，使用console.log()是一种更好的方式，原因在于：alert()函数会阻断JavaScript程序的执行，从而造成副作用；而console.log()仅在控制台中打印相关信息，因此不会造成类似的顾虑
---
#####一、什么是console.log()？

>除了一些很老版本的浏览器，现今大多数浏览器都自带调试功能；即使没有调试功能，也可以通过安装插件来进行补充。比如，老版本的Firefox没有自带调试工具，在这种情况下可以通过安装Firebug插件来添加调试功能。在具备调试功能的浏览器上，window对象中会注册一个名为console的成员变量，指代调试工具中的控制台。通过调用该console对象的log()函数，可以在控制台中打印信息。比如，以下代码将在控制台中打印”Sample log”：
>```
>window.console.log("Sample log");
>```
>也可以忽略Windows对象简写为
>```
>console.log("Sample log");
>```
>console.log()可以接受任何字符串、数字和JavaScript对象。与alert()函数类似，console.log()也可以接受换行符\n以及制表符\t。console.log()语句所打印的调试信息可以在浏览器的调试控制台中看到。不同的浏览器中console.log()行为可能会有所不同    

#####二、兼容没有调试控制台的浏览器    

>对于缺少调试控制台的老版本浏览器，window中的console对象并不存在，因此直接使用console.log()语句可能会在浏览器内部造成错误(空指针错误)，并最终导致某些老版本浏览器的崩溃。为了解决这一问题，可以人为定义console对象，并声明该console对象的log函数为空函数；这样，当console.log()语句执行时，这些老版本的浏览器将不会做任何事情：
>```
>if(!window.console){
  window.console = {log : function(){}};
}
>```
>不过，在多数情况下，没有必要去做这种工作  console.log()等调试代码应当从最终的产品代码中删除掉。.

#####三、使用参数

>与alert()函数类似，console.log()也可以接受变量并将其与别的字符串进行拼接：
>```
>var name = "Bob";
console.log("The name is: " + name);
```
>与alert()函数不同的是，console.log()还可以接受变量作为参数传递到字符串中
>```
>var people = "Alex";
var years = 42;
console.log("%s is %d years old.", people, years);
>```
>代码的执行结果为：”Alex is 42 years old.”

#####四、使用其它日志级别  

>除了console.log()，Firebug(火虫)还支持多种不同的日志级别：debug、info、warn、error。
>```
>Use different logging level
console.log("Log level");
console.debug("Debug level");
console.info("Info level");
console.warn("Warn level");
console.error("Error level");
>```
>从Firebug控制台中可以看到，不同日志级别的打印信息，其颜色和图标是不一样的；同时，可以在控制台中选择不同的日志级别来对这些信息进行过滤    
>![Alt text](./不同日志级别.png)
