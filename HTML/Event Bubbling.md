###JS冒泡事件
#### 1.冒泡型事件：事件按照从最特定的事件目标到最不特定的事件目标(document对象)的顺序触发。
  IE 5.5: div -> body -> document
  IE 6.0: div -> body -> html -> document
  Mozilla 1.0: div -> body -> html -> document -> window
 #### 2.支持W3C标准的浏览器在添加事件时用addEventListener(event,fn,useCapture)方法，基中第3个参数useCapture是一个Boolean值，用来设置事件是在事件捕获时执行，还是事件冒泡时执行。而不兼容W3C的浏览器(IE)用attachEvent()方法，此方法没有相关设置，不过IE的事件模型默认是在事件冒泡时执行的，也就是在useCapture等于false的时候执行，所以把在处理事件时把useCapture设置为false是比较安全，也实现兼容浏览器的效果。
####3.假设一个元素div，它有一个下级元素p。
、、、
<div>
　　<p>元素</p>
</div>
、、、
这两个元素都绑定了click事件，如果用户点击了p，它在div和p上都触发了click事件，那么在事件冒泡中，最具体的p先执行，然后到最不具体的div
#### 3.W3C模型是将两者进行中和，在W3C模型中，任何事件发生时，先从顶层开始进行事件捕获，直到事件触发到达了事件源元素。然后，再从事件源往上进行事件冒泡，直到到达document。
程序员可以自己选择绑定事件时采用事件捕获还是事件冒泡，方法就是绑定事件时通过addEventListener函数，它有三个参数，第三个参数若是true，则表示采用事件捕获，若是false，则表示采用事件冒泡。
ele.addEventListener('click',doSomething2,true)
true=捕获
false=冒泡
#### 4.IE浏览器
如上面所说，IE只支持事件冒泡，不支持事件捕获，它也不支持addEventListener函数，不会用第三个参数来表示是冒泡还是捕获，它提供了另一个函数attachEvent。
ele.attachEvent("onclick", doSomething2);
#### 5. 
1. 在W3c中，使用stopPropagation（）方法
2.  在IE下设置cancelBubble = true；在捕获的过程中stopPropagation（）；后，后面的冒泡过程也不会发生了~
3.阻止事件的默认行为，例如click <a>后的跳转~
4. 在W3c中，使用preventDefault（）方法；
5. 在IE下设置window.event.returnValue = false;