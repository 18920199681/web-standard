# VUE 规范

* #### 单文件组件，顶级元素的顺序

``` vue
<template></template>
<script></script>
<style></style>
```

<font style="color: red">* style只能在最下面，script和template至少要有一个</font>

* #### 除顶级 App 组件和布局组件中的样式可以是全局的，其它组件都应该为 style 标签加上 scoped，以保证样式不被污染

* #### v-for 循环必须加上 key 属性，涉及增删改操作的尽量不要使用下标作为 key

``` 

<ul>
  <li v-for="(item,index) in list" :key="index">
    {{ item.value }}
  </li>
</ul>
```

* #### 避免 v-if 和 v-for 同时用在一个元素上

v-for比v-if优先级高，所以使用的话，每次v-for都会执行v-if, 造成不必要的计算，影响性能，尤其是当之需要渲染很小一部分的时候。

* #### props 定义应该尽量详细

不推荐

``` javascript
props: {
  status: 'success'
}
```

推荐

``` javascript
props: {
  status: {
    type: String,
    defaut: "success"
  }
}
```

* #### 组件选项建议顺序

> components
> props
> data
> computed
> watch
> created
> mounted
> metods
> updated
> beforeDestroy
