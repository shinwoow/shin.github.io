# vue组件通信的6种方式

### 1. props + $emit	（父子组件通信）

该方式是日常开发种最常使用到的组件通信方式，子组件可以使用props接收父组件传递下来的属性，同时可以使用$emit先父组件传递自己的属性。对于需要传递的属性，开发者可以自定义，如果需要传递的属性较多，或者需要多级传递同样的属性，该方式的弊端就显而易见了。

```html
// parent.vue
<template>
	<child :name="'zhangsan'" greet="hello" @handleClick="parentHandleClick"></child>
</template>

<script>
export default {
    method: {
        parentHandleClick(arg1, arg2) { // 点击子组件的div后触发
            console.log(`parent.vue get ${arg1} ${arg2}!!!`) // parent.vue get a apple!!!
        }
    }
}
</script>
```

```html
// child.vue
<template>
    <div @click="handleClick">{{greet}} {{name}}!!!</div>
</template>

<script>
export default {
    props: {
        name: "",
        greet: ""
    }
    data() {
        someArg: "a",
        otherArg: "apple"
    }
    methods: {
        handleClick() {
            // do something
            this.$emit('handleClick', someArg, otherArg); // 触发父组件的handleClick方法并传递两个arg
        }
    }
}
</script>
```



### 2. provide + inject	（向后代组件传值）

在vue的官方文档中不推荐使用这种组件通信方式，对于多级组件通信而言，该方式显的有点隐晦，在代码出现问题时，很难及时的定位到问题代码的位置。但是有很多的开发团队直接使用或者自己开发了类似功能的通信方式，这种通信方式在多级组件开发中具有显著的优势，由于是组件开发，也几乎不存在前面所述的问题。所以该方式在复杂组件的开发中显得十分快速有效。



### 3. $attr + $listen	（祖先、后代组件通信）

与provide + reject的通信方式相比，该方式需要在每一级都添加$attr和$listen，在代码中显示出的逻辑性更强，同样可以

后代与祖先组件通信

### 4. $children + $parent	（祖先、后代组件通信）

后代与祖先租价通信	

由于能够直接修改祖先组件的值，可能导致代码逻辑混乱，最好不要用，除非忍不住。

### 5. vuex	（所有组件间通信）

后代与祖先、兄弟组件通信

vuex是vue的状态管理模块，开发者可以选择是否使用该功能，

### 6. eventBus	（所有组件间通信）

同上

对于小型应用而言，使用vuex显得过于累赘，那么使用eventBus不失为一种优秀的通信方式

