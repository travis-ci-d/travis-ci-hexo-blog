title: vue编码训诫
date: 2017-11-10T04:06:45.414Z
tags: []
categories: []
---
*单向数据流*
---
> Prop 是单向绑定的：当父组件的属性变化时，将传导给子组件，但是反过来不会。
> 这是为了防止子组件无意间修改了父组件的状态，来避免应用的数据流变得难以理解。
> 另外，每次父组件更新时，子组件的所有 prop 都会更新为最新值。
> 这意味着你不应该在子组件内部改变 prop。如果你这么做了，Vue 会在控制台给出警告。
> 在两种情况下，我们很容易忍不住想去修改 prop 中数据：
> Prop 作为初始值传入后，子组件想把它当作局部数据来用；
> Prop 作为原始数据传入，由子组件处理成其它数据输出。
> 对这两种情况，正确的应对方式是：
> 定义一个局部变量，并用 prop 的值初始化它：

  ``` 
  props: ['initialCounter'],
  data: function () {
    return { counter: this.initialCounter }
  }

// 定义一个计算属性，处理 prop 的值并返回：

  props: ['size'],
  computed: {
    normalizedSize: function () {
      return this.size.trim().toLowerCase()
    }
  }
```

> 注意在 JavaScript 中对象和数组是引用类型，指向同一个内存空间，
> 如果 prop 是一个对象或数组，在子组件内部改变它会影响父组件的状态。