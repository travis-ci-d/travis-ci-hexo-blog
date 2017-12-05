title: vue文档语录
date: 2017-11-07T02:14:50.581Z
tags: []
categories: []
---
# Vue 2.0
## Vue 实例
### 创建一个-Vue-的实例
- 每个 Vue 应用都是通过 Vue 函数创建一个新的 Vue 实例开始的；
+ 虽然没有完全遵循 MVVM 模型，Vue 的设计无疑受到了它的启发。
  - 因此在文档中经常会使用 vm (ViewModel 的简称) 这个变量名表示 Vue 实例。
  - 当创建一个 Vue 实例时，你可以传入一个选项对象。
  - 作为参考，你也可以在 API 文档 中浏览完整的选项列表。
+ 一个 Vue 应用由一个通过 new Vue 创建的根 Vue 实例，
  -   以及可选的嵌套的、可复用的组件树组成。

### 数据与方法
+ 当一个 Vue 实例被创建时，
  - 它向 Vue 的响应式系统中加入了其 data 对象中能找到的所有的属性。
  - 当这些属性的值发生改变时，
  - 视图将会产生“响应”，即匹配更新为新的值。
  - 只有当实例被创建时 data 中存在的属性是响应式的。
  - 那么对 b 的改动将不会触发任何视图的更新。
  - 如果你知道你会在晚些时候需要一个属性，
  - 但是一开始它为空或不存在，
  - 那么你仅需要设置一些初始值。

+ 除了 data 属性，
  - Vue 实例暴露了一些有用的实例属性与方法。
  - 它们都有前缀 $，
  - 以便与用户定义的属性区分开来。
  - 在未来，你可以在 API 参考查阅到完整的实例属性和方法的列表。

### 实例生命周期
+ 每个 Vue 实例在被创建之前都要经过一系列的初始化过程。
  - 例如需要设置数据监听、编译模板、挂载实例到 DOM、在数据变化时更新 DOM 等。
  - 同时在这个过程中也会运行一些叫做生命周期钩子的函数，
  - 给予用户机会在一些特定的场景下添加他们自己的代码。
  - '比如 created 钩子可以用来在一个实例被创建之后执行代码;'
+ 也有一些其它的钩子，
  -   在实例生命周期的不同场景下调用，
+ 如 mounted、updated、destroyed。钩子的 this 指向调用它的 Vue 实例。    
  - 不要在选项属性或回调上使用箭头函数；
  - 因为箭头函数是和父级上下文绑定在一起的，
  - this 不会是如你所预期的 Vue 实例，
  - 经常导致 Uncaught TypeError: Cannot read property of undefined,
  - 或 Uncaught TypeError: this.myMethod is not a function 之类的错误。
+ 生命周期图示    
  - 下图说明了实例的生命周期。
  - 你不需要立马弄明白所有的东西，
  - 不过随着你的不断学习和使用，
  - 它的参考价值会越来越高。
    
![vue生命周期](https://cn.vuejs.org/images/lifecycle.png)

## 模板语法
+ Vue.js 使用了基于 HTML 的模板语法，
  - 允许开发者声明式地将 DOM 绑定至底层 Vue 实例的数据。
  - 所有 Vue.js 的模板都是合法的 HTML ，
  - 所以能被遵循规范的浏览器和 HTML 解析器解析。
+ 在底层的实现上，
  - Vue 将模板编译成虚拟 DOM 渲染函数。
  - 结合响应系统，在应用状态改变时，
  - Vue 能够智能地计算出重新渲染组件的最小代价并应用到 DOM 操作上。
+ 如果你熟悉虚拟 DOM 并且偏爱 JavaScript 的原始力量，
  - 你也可以不用模板，
  - 直接写渲染 (render) 函数，
  - 使用可选的 JSX 语法。

### 插值
#### 文本
- 数据绑定最常见的形式就是使用“Mustache”语法 (双大括号) 的文本插值;
+ Mustache 标签将会被替代为对应数据对象上 msg 属性的值。
  - 无论何时，
  - 绑定的数据对象上 msg 属性发生了改变，
  - 插值处的内容都会更新。
+ 通过使用 v-once 指令，
  - 你也能执行一次性地插值，
  - 当数据改变时，插值处的内容不会更新。
  - 但请留心这会影响到该节点上所有的数据绑定:
  - <span v-once>这个将不会改变: {{ msg }}</span>
    
## 计算属性和观察者

### 计算属性

+ 模板内的表达式非常便利，
  - 但是设计它们的初衷是用于简单运算的。
  - 在模板中放入太多的逻辑会让模板过重且难以维护, 如：
```
  <div id="example">  {{ message.split('').reverse().join('') }}  </div>
```
+ 在这个地方，模板不再是简单的声明式逻辑。
  - 你必须看一段时间才能意识到，
  - 这里是想要显示变量 message 的翻转字符串。
  - 当你想要在模板中多次引用此处的翻转字符串时，就会更加难以处理。
  - 所以，'对于任何复杂逻辑，你都应当使用计算属性。'    

1. 
#### [基础例子](https://cn.vuejs.org/v2/guide/computed.html#基础例子)
1. 
#### [计算属性缓存 vs 方法](https://cn.vuejs.org/v2/guide/computed.html#计算属性缓存-vs-方法)   
1. 
#### [计算属性 vs 侦听属性](https://cn.vuejs.org/v2/guide/computed.html#计算属性-vs-侦听属性)
1. 
#### [计算属性的 setter](https://cn.vuejs.org/v2/guide/computed.html#计算属性的-setter)

### 侦听器
+ 虽然计算属性在大多数情况下更合适，
  - 但有时也需要一个自定义的侦听器。
  - 这就是为什么 Vue 通过 watch选项提供了一个更通用的方法，来响应数据的变化。
  - 当需要在数据变化时执行异步或开销较大的操作时，这个方式是最有用的。
+ watch 选项允许我们执行异步操作 (访问一个 API)，
  - 限制我们执行该操作的频率，
  - 并在我们得到最终结果前，设置中间状态。
  - 这些都是计算属性无法做到的。    
  - 除了 watch 选项之外，您还可以使用命令式的 vm.$watch API。    

## Class 与 Style 绑定

+ 操作元素的 class 列表和内联样式是数据绑定的一个常见需求。
  - 因为它们都是属性，所以我们可以用 v-bind 处理它们：
  - 只需要通过表达式计算出字符串结果即可。
  - 不过，字符串拼接麻烦且易错。
  - 因此，在将 v-bind 用于 class 和 style 时，Vue.js 做了专门的增强。
  - 表达式结果的类型除了字符串之外，还可以是对象或数组。

+ 绑定 HTML Class
 + [#对象语法](https://cn.vuejs.org/v2/guide/class-and-style.html#对象语法)
  + 我们可以传给 v-bind:class 一个对象，以动态地切换 class;
   - 上面的语法表示 active 这个 class 存在与否将取决于数据属性 isActive 的 truthiness。
   - 你可以在对象中传入更多属性来动态切换多个 class，
   - 此外，v-bind:class 指令也可以与普通的 class 属性共存。
   - 绑定的数据对象不必内联定义在模板里;
   + 渲染的结果和上面一样。
    - '我们也可以在这里绑定一个返回对象的计算属性,这是一个常用且强大的模式';
 + [#数组语法](https://cn.vuejs.org/v2/guide/class-and-style.html#数组语法)
  + 我们可以把一个数组传给 v-bind:class，以应用一个 class 列表;
   - 如果你也想根据条件切换列表中的 class，可以用三元表达式;
   - 不过，当有多个条件 class 时这样写有些繁琐。
   - 所以在数组语法中也可以使用对象语法;
 + [#用在组件上](https://cn.vuejs.org/v2/guide/class-and-style.html#用在组件上)
  - '当在一个自定义组件上使用 class 属性时，'
  - '这些类将被添加到根元素上面。'
  - '这个元素上已经存在的类不会被覆盖。'
  - '对于带数据绑定 class 也同样适用; '

## 绑定内联样式
### [#对象语法](https://cn.vuejs.org/v2/guide/class-and-style.html#对象语法-1) 
+ v-bind:style 的对象语法十分直观——看着非常像 CSS，
 - 但其实是一个 JavaScript 对象。
 - CSS 属性名可以用驼峰式 (camelCase) 或短横线分隔 (kebab-case，记得用单引号括起来) 来命名;
 - 直接绑定到一个样式对象通常更好，这会让模板更清晰;
 - 同样的，对象语法常常结合返回对象的计算属性使用。
### [#数组语法](https://cn.vuejs.org/v2/guide/class-and-style.html#数组语法-1) 
 - v-bind:style 的数组语法可以将多个样式对象应用到同一个元素上;
### [#自动添加前缀](https://cn.vuejs.org/v2/guide/class-and-style.html#自动添加前缀) 
 - 当 v-bind:style 使用需要添加浏览器引擎前缀的 CSS 属性时，如 transform，Vue.js 会自动侦测并添加相应的前缀。
### [#多重值](https://cn.vuejs.org/v2/guide/class-and-style.html#多重值) 
 + 从 2.3.0 起你可以为 style 绑定中的属性提供一个包含多个值的数组，
  - 常用于提供多个带前缀的值;

## 条件渲染
### [v-if](https://cn.vuejs.org/v2/guide/conditional.html#v-if)
### [在-lt-template-gt-元素上使用-v-if-条件渲染分组](https://cn.vuejs.org/v2/guide/conditional.html#在-lt-template-gt-元素上使用-v-if-条件渲染分组) 
+ 因为 v-if 是一个指令，所以必须将它添加到一个元素上。
 - 但是如果想切换多个元素呢？
 - 此时可以把一个 <template> 元素当做不可见的包裹元素，并在上面使用 v-if。
 - 最终的渲染结果将不包含 <template> 元素。
### [v-else](https://cn.vuejs.org/v2/guide/conditional.html#v-else)  
+ 可以使用 v-else 指令来表示 v-if 的“else 块”;
 - v-else 元素必须紧跟在带 v-if 或者 v-else-if 的元素的后面，否则它将不会被识别。
### [v-else-if](https://cn.vuejs.org/v2/guide/conditional.html#v-else-if)  
> 2.1.0 新增
+ v-else-if，顾名思义，充当 v-if 的“else-if 块”，可以连续使用;
 - 类似于 v-else，v-else-if 也必须紧跟在带 v-if 或者 v-else-if 的元素之后。

### [用key管理可复用的元素](https://cn.vuejs.org/v2/guide/conditional.html#用-key-管理可复用的元素) 
+ Vue 会尽可能高效地渲染元素，通常会复用已有元素而不是从头开始渲染。
 - 这么做除了使 Vue 变得非常快之外，还有其它一些好处: (局部更新DOM)[笔者注]。
 + 这样也不总是符合实际需求，
   - 所以 Vue 为你提供了一种方式来表达"这两个元素是完全独立的，不要复用它们"(递归替换key属性所在的元素)[笔者注]。
   - 只需添加一个具有唯一值的 key 属性即可,
   - 每次切换时，输入框都将被重新渲染。

### [v-show](https://cn.vuejs.org/v2/guide/conditional.html#v-show)  
+ 另一个用于根据条件展示元素的选项是 v-show 指令。
 - 不同的是带有 v-show 的元素始终会被渲染并保留在 DOM 中。
 - v-show 只是简单地切换元素的 CSS 属性 display。
 - '注意，v-show 不支持 <template> 元素，也不支持 v-else'。

### [v-if vs v-show](https://cn.vuejs.org/v2/guide/conditional.html#v-if-vs-v-show) 
+ v-if 是“真正”的条件渲染，
 - 因为它会确保在切换过程中条件块内的事件监听器和子组件适当地被销毁和重建。
+ v-if 也是惰性的：如果在初始渲染时条件为假，
 - 则什么也不做——直到条件第一次变为真时，
 - 才会开始渲染条件块。
+ 相比之下，v-show 就简单得多——不管初始条件是什么，
 - 元素总是会被渲染，
 - 并且只是简单地基于 CSS 进行切换。
 + 一般来说，
 - v-if 有更高的切换开销，
 - 而 v-show 有更高的初始渲染开销。
 + 因此，
 - 如果需要非常频繁地切换，
 - 则使用 v-show 较好；
 + 如果在运行时条件很少改变，
 - 则使用 v-if 较好。

### [v-if与v-for-一起使用](https://cn.vuejs.org/v2/guide/conditional.html#v-if-与-v-for-一起使用)
+ 当 v-if 与 v-for 一起使用时，
 - v-for 具有比 v-if 更高的优先级。
  
## [列表渲染](https://cn.vuejs.org/v2/guide/list.html)  

### [用v-for把一个数组对应为一组元素](https://cn.vuejs.org/v2/guide/list.html#用-v-for-把一个数组对应为一组元素)
+ 我们用 v-for 指令根据一组数组的选项列表进行渲染。
 - v-for 指令需要使用 item in items 形式的特殊语法，
 - items 是源数据数组并且 item 是数组元素迭代的别名。
+ 在 v-for 块中，
 - 我们拥有对父作用域属性的完全访问权限。
 - v-for 还支持一个可选的第二个参数为当前项的索引。 
 - (实战中编译时可能出错,建议不用of,只用in)[笔者注]你也可以用 of 替代 in 作为分隔符，因为它是最接近 JavaScript 迭代器的语法;

### [一个对象的-v-for](https://cn.vuejs.org/v2/guide/list.html#一个对象的-v-for) 
+ 你也可以用 v-for 通过一个对象的属性来迭代。
 - 也可以提供第二个的参数为键名
 - 第三个参数为索引 
> 在遍历对象时，
> 是按 Object.keys() 的结果遍历，
> 但是不能保证它的结果在不同的 JavaScript 引擎下是一致的。 

### [key](https://cn.vuejs.org/v2/guide/list.html#key)

+ 当 Vue.js 用 v-for 正在更新已渲染过的元素列表时，
 - 它默认用“就地复用”策略。

+ 如果数据项的顺序被改变，
 - Vue 将不会移动 DOM 元素来匹配数据项的顺序，
 - 而是简单复用此处每个元素，
 - 并且确保它在特定索引下显示已被渲染过的每个元素。
 - 这个类似 Vue 1.x 的 track-by="$index" 。

+ 这个默认的模式是高效的，
 - 但是只适用于不依赖子组件状态或临时 DOM 状态 (例如：表单输入值) 的列表渲染输出。

+ 为了给 Vue 一个提示，
 + 以便它能跟踪每个节点的身份，
  - 从而重用和重新排序现有元素，你需要为每项提供一个唯一 key 属性。
  - 理想的 key 值是每项都有的且唯一的 id。
  - 这个特殊的属性相当于 Vue 1.x 的 track-by ，
  - 但它的工作方式类似于一个属性，
  - 所以你需要用 v-bind 来绑定动态值 (在这里使用简写);
 + 建议尽可能在使用 v-for 时提供 key，
  - 除非遍历输出的 DOM 内容非常简单，
  - 或者是刻意依赖默认行为以获取性能上的提升。
 + 因为它是 Vue 识别节点的一个通用机制，
  - key 并不与 v-for 特别关联，
  - key 还具有其他用途，
  - 我们将在后面的指南中看到其他用途。 

### [数组更新检测](https://cn.vuejs.org/v2/guide/list.html#数组更新检测) 

#### [变异方法](https://cn.vuejs.org/v2/guide/list.html#变异方法)
+ Vue 包含一组观察数组的变异方法，所以它们也将会触发视图更新。这些方法如下：
 - push()
 - pop()
 - shift()
 - unshift()
 - splice()
 - sort()
 - reverse()

#### [替换数组](https://cn.vuejs.org/v2/guide/list.html#替换数组)
+ 变异方法 (mutation method)，
 - 顾名思义，会改变被这些方法调用的原始数组。

#### 相比之下，也有非变异 (non-mutating method) 方法，
 + 例如：filter(), concat() 和 slice() 。
  - 这些不会改变原始数组，但总是返回一个新数组。
  - 当使用非变异方法时，可以用新数组替换旧数组(覆盖式赋值)[笔者注]；
　
#### [注意事项](https://cn.vuejs.org/v2/guide/list.html#注意事项)
 + 由于 JavaScript 的限制，Vue 不能检测以下变动的数组：
  - 当你利用索引直接设置一个项时，例如：vm.items[indexOfItem] = newValue
  - 当你修改数组的长度时，例如：vm.items.length = newLength
 + 为了解决第一类问题，
  - 以下两种方式都可以实现和 vm.items[indexOfItem] = newValue 相同的效果，
  + 同时也将触发状态更新:
    
    - eg 1: 
    ```
    // Vue.set
　　Vue.set(example1.items, indexOfItem, newValue)
    ```
    
    - eg 2:
    ```
    // Array.prototype.splice
    example1.items.splice(indexOfItem, 1, newValue)
    ```
  + 为了解决第二类问题，可以使用 splice：
    ```
    example1.items.splice(newLength);   
    ```

#### [对象更改检测注意事项](https://cn.vuejs.org/v2/guide/list.html#对象更改检测注意事项)
 - 还是由于 JavaScript 的限制，Vue 不能检测对象属性的添加或删除;
 + 对于已经创建的实例，Vue 不能动态添加根级别的响应式属性。
  - 但是，可以使用 Vue.set(object, key, value) 方法向嵌套对象添加响应式属性。
  - 你还可以使用 vm.$set 实例方法，它只是全局 Vue.set 的别名;
 + 有时你可能需要为已有对象赋予多个新属性，
  - 比如使用 Object.assign() 或 _.extend()。
  - 在这种情况下，你应该用两个对象的属性创建一个新的对象。
  - 你应该这样做：
   ```
    this.userProfile = Object.assign({}, this.userProfile, {
     age: 27,
     favoriteColor: 'Vue Green'
    })
   ```

### [显示过滤/排序结果](https://cn.vuejs.org/v2/guide/list.html#显示过滤-排序结果)
+ 有时，我们想要显示一个数组的过滤或排序副本，
 - 而不实际改变或重置原始数据。
 - 在这种情况下，可以创建返回过滤或排序数组的计算属性。
 - 在计算属性不适用的情况下 (例如，在嵌套 v-for 循环中) 你可以使用一个 method 方法;
### [一段取值范围的v-for](https://cn.vuejs.org/v2/guide/list.html#一段取值范围的-v-for) 
 - v-for 也可以取整数。在这种情况下，它将重复多次模板。
### [v-for on a <template>](https://cn.vuejs.org/v2/guide/list.html#v-for-on-a-lt-template-gt) 
 - 类似于 v-if，你也可以利用带有 v-for 的 <template> 渲染多个元素。
### [v-for with v-if](https://cn.vuejs.org/v2/guide/list.html#v-for-with-v-if) 
 + 当它们处于同一节点，v-for 的优先级比 v-if 更高，
  - 这意味着 v-if 将分别重复运行于每个 v-for 循环中。
  - 当你想为仅有的一些项渲染节点时，
  - 这种优先级的机制会十分有用;
 + 而如果你的目的是有条件地跳过循环的执行，
  - 那么可以将 v-if 置于外层元素 (或 <template>)上。 
### [一个组件的v-for](https://cn.vuejs.org/v2/guide/list.html#一个组件的-v-for)   
 + 在自定义组件里，
  - 你可以像任何普通元素一样用 v-for 。
 + 然而，任何数据都不会被自动传递到组件里，
  - 因为组件有自己独立的作用域。
  - 为了把迭代数据传递到组件里，
  - 我们要用 props;
 + 不自动将 item 注入到组件里的原因是，
  - 这会使得组件与 v-for 的运作紧密耦合。
  - 明确组件数据的来源能够使组件在其他场合重复使用。 
 + 下面是一个简单的 todo list 的完整例子：
 ```
 <div id="todo-list-example">
  <input
    v-model="newTodoText"
    v-on:keyup.enter="addNewTodo"
    placeholder="Add a todo"
  >
  <ul>
    <li
      is="todo-item"
      v-for="(todo, index) in todos"
      v-bind:key="todo.id"
      v-bind:title="todo.title"
      v-on:remove="todos.splice(index, 1)"
    ></li>
  </ul>
</div>
 ```
> 注意这里的 is="todo-item" 属性。
> 这种做法在使用 DOM 模板时是十分必要的，
> 因为在 <ul> 元素内只有 <li> 元素会被看作有效内容。
> 这样做实现的效果与 <todo-item> 相同，
> 但是可以避开一些潜在的浏览器解析错误。
> 查看 [DOM 模板解析](https://cn.vuejs.org/v2/guide/components.html#DOM-模板解析说明) 说明 来了解更多信息。 

## [事件处理](https://cn.vuejs.org/v2/guide/events.html)

### [监听事件](https://cn.vuejs.org/v2/guide/events.html#监听事件)
> 可以用 v-on 指令监听 DOM 事件来触发一些 JavaScript 代码。

### [方法事件处理器](https://cn.vuejs.org/v2/guide/events.html#方法事件处理器)
> 许多事件处理的逻辑都很复杂，
> 所以直接把 JavaScript 代码写在 v-on 指令中是不可行的。
> 因此 v-on 可以接收一个定义的方法来调用。

### [内联处理器里的方法](https://cn.vuejs.org/v2/guide/events.html#内联处理器里的方法)
> 除了直接绑定到一个方法，也可以用内联 JavaScript 语句:
```
 <button v-on:click="say('hi')">Say hi</button>
```
> 有时也需要在内联语句处理器中访问原生 DOM 事件。
> 可以用特殊变量 $event 把它传入方法, eg:
```
// template
<button v-on:click="warn('Form cannot be submitted yet.', $event)">
  Submit
</button>

// ...
methods: {
  warn: function (message, event) {
    // 现在我们可以访问原生事件对象
    if (event) event.preventDefault()
    alert(message)
  }
}
```

[事件修饰符](https://cn.vuejs.org/v2/guide/events.html#事件修饰符)

1. 
> 在事件处理程序中调用 event.preventDefault() 或 event.stopPropagation() 是非常常见的需求。
> 尽管我们可以在 methods 中轻松实现这点，
> 但更好的方式是：methods 只有纯粹的数据逻辑，
> 而不是去处理 DOM 事件细节。

1. 
> ### 为了解决这个问题，Vue.js 为 v-on 提供了事件修饰符。
> 通过由点 (.) 表示的指令后缀来调用修饰符。

1. 
> ##### .stop
> ##### .prevent
> ##### .capture
> ##### .self
> ##### .once
