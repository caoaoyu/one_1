###jQuery 事件 - trigger() 方法
##### 根据绑定到匹配元素的给定的事件类型执行所有的处理程序和行为。
---
>当相应的事件发生时，任何通过.on或一个快捷方法绑定的事件处理程序将被触发。调用.trigger（）执行处理程序和用户自然的触发该事件，他们的执行顺序时相同的
>```
>$('#foo').on('click', function() {
  >    alert($(this).text());
   > });
   > $('#foo').trigger('click');
>```
>从jQuery 1.3开始，.trigger()事件会在DOM树上冒泡;在事件处理程序中返回false或调用事件对象中的.stopPropagation() 方法可以使事件停止冒泡。尽管 .trigger() 模拟了事件的激活，具备合成的 event 对象，但是它并没有完美的复制自然发生的事件（naturally-occurring event）。

>若要触发通过 jQuery 绑定的事件处理函数，而不触发原生的事件，使用.triggerHandler() 来代替。

>当我们使用.on()方法定义一个自定义事件类型，.trigger()的第二个参数就有用了。例如，假设我们自定义事件的处理程序绑定到我们的元素而不是内置的click事件
>```
$('#foo').on('custom', function(event, param1, param2) {
  alert(param1 + "\n" + param2);
});
$('#foo').trigger('custom', ['Custom', 'Event']);
>```
>事件对象始终是被传递到事件处理程序的第一个参数，但如果指定了额外的参数调用.trigger() 时，这些参数将被传递给处理程序。要传递多个参数，使用一个数组，如下所示。从jQuery 1.6.2开始，可以通过一个单一的参数，而不使用一个数组。
>请注意向该方法中传入的 extraParameters 参数与传入到 .on() 方法中的 eventData 参数的区别。它们的机制都是向事件处理函数中传入信息，但是传入 .trigger() 中的 extraParameters 参数是在事件发生时传入的，而传入到 .on() 中的 eventData 参数要求在进行事件绑定时就要事先计算好。
>.trigger() 方法可以应用在包裹简单 JavaScript 对象的 jQuery 集合中，类似 pub/sub 机制(观察者机制)。当事件发生时，任何绑定在对象上的处理函数都会被触发。
>>1.注意: 对于非window的普通的对象和DOM对象， 如果一个触发事件名称和对象的一个属性名称相匹配， 如果事件处理程序没有调用event.preventDefault()，jQuery将尝试调用属性的方法。 如果不希望这种行为发生，请使用.triggerHandler() 来代替。（愚人码头注 .triggerHandler() 方法并不会触发事件的默认行为。
>
>>2.注意: 和.triggerHandler()一样， 当调用.trigger()时，当一个事件名称匹配对象上属性名称时，属性名称会加上on前缀（如，在 具有非空onclick方法的window上触发click），  jQuery将尝试调用该属性作为方法。
>>3.注意: 当通过一个普通的对象不是类数组触发时 但仍然包含了length属性， 你应该传递对象到数组中（例如：[ { length: 1 } ]）。
######Example: 点击 button #2 时，同时触发 button #1 的点击事件。
>``` 
>button { margin:10px; }
>div { color:blue; font-weight:bold; }
>span { color:red; }
>  <button>Button #1</button>
><button>Button #2</button>
><div><span>0</span> button #1 clicks.</div>
 
><div><span>0</span> button #2 clicks.</div>

>$("button:first").click(function () {
>update($("span:first"));
>});
>$("button:last").click(function () {
>$("button:first").trigger('click');
 
>update($("span:last"));
>});
 
>function update(j) {
>var n = parseInt(j.text(), 10);
>j.text(n + 1);
>}
>```
######Example: 若要提交第一个表单但又不想使用 submit() 函数，请尝试如下方法：
>```
>$("form:first").trigger("submit")
>```
######Example: 向事件中传入任意的数据：
>```
>$("p").click( function (event, a, b) { 
>} ).trigger("click", ["foo", "bar"]);
>```
######Example: 通过 event 对象，向事件中传入任意的数据：span>
>```
>var event = jQuery.Event("logged");
>event.user = "foo";
>event.pass = "bar";
>$("body").trigger(event);
>```
######Example: 另外一种通过 event 对象传入数据的方法：
>```
>$("body").trigger({
>type:"logged",
>user:"foo",
>pass:"bar"
 >});
>```
