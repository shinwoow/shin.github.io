上次面试鹅厂，过程相当凄惨，深感自己基础知识不牢固，为此也埋下了许多祸端，所以毅然决然的决定研究vue的源代码，发现了yyx大神的不少优秀之处，特做笔记记录

在源码中有一个repeat函数使用了一个前所未见的符号>>=百思不得其解，百度搜索对于这种符号也不敏感，发了个帖子问了圈内大佬才得到一点启发，这个符号表示将数据的二进制右移一位，再赋值给自身，代码如下
<pre>
  <code>
    var repeat = function (str, n) {
      var res = '';
      while (n) {
        if (n % 2 === 1) { res += str; }
        if (n > 1) { str += str; }
        n >>= 1;
      }
      return res
    }
  </code>
</pre>
这个函数极为巧妙的将str复制了n遍，空间复杂度和时间复杂度都极低。

vue多处使用Object.create(null)创建新的空对象，这个方式抛弃了原型对象上的属性（toString、hasOwnPropert、 etc）都抛弃了，因为vue自己都重写了一份，目的时为了代码风格一致
