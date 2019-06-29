创建新的个人项目，发现自己写组件真的任务重大，还是用现成的好，看了几个vue组件库，比如：mint.ui/vonic, 以前的项目中移动端都是使用的vux，个人觉的不是很好看，别打我，PC端使用的element-ui还是很好看的。其实只是觉得Button的颜色不满意哈哈，看见vonic的按钮这他妈忒好看了，想用vonic，但组件的个数少了点，上一次更新在一年前了。难受
所以还是使用老搭档vux吧，照着官方文档一步一步来，安装vux，vux-load, less, less-load
<pre>
   <code>
      npm install vux vux-loader --save
      npm install less less-loader --save
   </code>
</pre>
配置webpack.base.cof
在App.vue中引入vux的reset.less
<pre>
   <javascript>
      <style lang='less'>
      @import '~vux/src/styles/reset.less'
      </style>
   </javascript>
</pre>
由于没有在style标签上加上<code>lang='less'</code>,导致<code>npm run dev</code>一直报错，提示找不到文件
正常引入后，与原本引入的reset.css冲突，使得部分样式出现问题，偏离屏幕，删除其他的css文件，恢复正常，但是部分vux的组件显示不正确，解决中。。。
