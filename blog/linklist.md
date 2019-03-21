# 关于js实现链表
最近学习了一下据结构与算法，里面提到了链表、队列这些概念，可惜是c++版的，不知道在js中怎么实现这些操作，百度了一番，发现都是使用**数组**实现的，对数组进行push、pop、unshift、shift，实现队列与链表，
push可以向数组的末尾插入一个数据，pop可以将最后一个元素取出来，而unshift可以将数组的第0位数据取出来，改变数组长度，shift可以插入一个数据到第0位，如下：

<pre>
  <code>
var list = [0,1,2,3]
var div = document.getElementById('div')
console.log(list)       //[0,1,2,3]
function testPush () {
  list.push(4)
  console.log(list)     //[0,1,2,3,4]
}
function testPop () {
  list.pop()
  console.log(list)     //[0,1,2,3]
}
function testUnshift () {
  list.unshift(5)
  console.log(list)     //[5,0,1,2,3]
}
function testShift () {
  list.shift()
  console.log(list)     //[0,1,2,3]
}</code>
</pre>
这确实是比较理想的链表和队列的实现方法，但总觉得与java，c++的比较起来有点捞
不久前在刷LeetCode的算法题，突然发现一个更加有B格的实现方法
<pre>
  <code>
  function ListNode(val) {
    this.val = val;
    this.next = null;
  }
  </code>
</pre>
ListNode.next = new ListNode(val)创建一个新的节点，遍历使用提供的next方法，瞬间感觉上了一个档次，当next属性为null时，则代表链表已经结束

