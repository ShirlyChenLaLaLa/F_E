
### 事件的一些小知识

#### DOM事件流包括三个阶段。

1. 事件捕获阶段
2. 处于目标阶段
3. 事件冒泡阶段

#### 事件冒泡

事件冒泡即事件开始时，由最具体的元素接收（也就是事件发生所在的节点），然后逐级传播到较为不具体的节点。
举个栗子，就很容易明白了。
button  ->  body  -> document -> window

#### 事件捕获
事件捕获的概念，与事件冒泡正好相反。它认为当某个事件发生时，父元素应该更早接收到事件，具体元素则最后接收到事件。
window  ->  document  -> body -> button

#### 事件委托
事件委托就是利用冒泡的原理，把事件加到父元素或祖先元素上，触发执行效果。

```javascript

var btn6 = document.getElementById("btn6");
document.onclick = function(event){
  event = event || window.event;
  var target = event.target || event.srcElement;
  if(target == btn6){
    alert(btn5.value);
  }
}

```
优点：
1. 提高JavaScript性能。事件委托可以显著的提高事件的处理速度，减少内存的占用。
2. 可以实现当新增子对象时无需再次对其绑定事件，对于动态内容部分尤为合适

缺点：
1. 事件代理的应用常用应该仅限于上述需求下，如果把所有事件都用代理就可能会出现事件误判，即本不应用触发事件的被绑上了事件。

