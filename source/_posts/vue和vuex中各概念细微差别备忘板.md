title: vue和vuex中各概念细微差别备忘板
date: 2017-10-27T02:56:56.376Z
tags: []
categories: []
---
* 
# vue实例：

*缓存，更新  *
    
    -   data 属性对象中定义的属性值会被缓存,不会随依赖变量变化而计算更新；

    -   computed 属性对象中定义的属性值会被缓存,会随依赖变量变化而计算更新；

    -   filter 属性对象中定义的属性值不会被缓存,会随依赖变量变化而计算更新；

    +   watch 属性对象中定义的属性值不会被缓存,
        -   会随在属性名'a'所对应的实例属性this['a']之变化时，
        -   执行watch中定义的'a'属性标示的函数；


* 
# vuex实例中的概念：

[*state 单一状态树*](https://vuex.vuejs.org/zh-cn/state.html)

    +   Vuex 通过 store 选项，
        -   '提供了一种机制将状态从根组件“注入”到每一个子组件中（需调用 Vue.use(Vuex)）';
        
    +   通过在根实例中注册 store 选项，
        -   该 store实例会注入到根组件下的所有子组件中，
        -   且子组件能通过 this.$store 访问到。;
        -   当一个组件需要获取多个状态时候，
        -   将这些状态都声明为计算属性会有些重复和冗余。
        -   为了解决这个问题，
        -   '可以使用 mapState 辅助函数帮助我们生成计算属性';
        -   当映射的计算属性的名称与 state 的子节点名称相同时，
        -   我们也可以给 mapState 传一个字符串数组。

[*getter*](https://vuex.vuejs.org/zh-cn/getters.html) 

    -   有时候我们需要从 store 中的 state 中派生出一些状态;

    +   如果有多个组件需要用到此属性，
        -   我们要么复制这个函数，
        -   或者抽取到一个共享函数然后在多处导入它,
        -   无论哪种方式都不是很理想;

    +   Vuex 允许我们在 store 中定义“getter”
        -   '可以认为getter是 store 的计算属性',
        -   就像计算属性一样;
        -   getter的返回值会根据它的依赖被缓存起来，
        -   而且且只有当它的依赖值发生了改变才会被重新计算;

    -   Getter 接受 state 作为其第一个参数;

    -   Getter 会暴露为 store.getters 对象;

    -   Getter 也可以接受其他 getter 作为第二个参数;

    -   我们可以很容易地在任何组件中使用它;

    +   也可以通过让 getter 返回一个函数，
        -   来实现给 getter 传参,
        -   在对 store 里的数组进行查询时非常有用;

    +   mapGetters 辅助函数仅仅是将 store 中的 getter 映射到局部计算属性;    
        -   如果想将一个 getter 属性另取一个名字，
        -   使用对象形式;
        
[*Mutation*](https://vuex.vuejs.org/zh-cn/mutations.html)
    
    +   更改 Vuex 的 store 中的状态的唯一方法是提交 mutation;
        +   Vuex 中的 mutation 非常类似于事件：
            -   每个 mutation 都有一个字符串的 事件类型 (type),
            -   一个 回调函数 (handler);
        +   这个回调函数就是我们实际进行状态更改的地方，
            -   并且它会接受 state 作为第一个参数;
            
    +   你不能直接调用一个 mutation handler。
        +   这个选项更像是事件注册：“当触发一个类型为 increment 的 mutation 时，调用此函数。”;
            -   要唤醒一个 mutation handler，
            -   你需要以相应的 type 调用 store.commit 方法：            
            
    +   提交载荷（Payload）
        +   你可以向 store.commit 传入额外的参数，即 mutation 的 载荷（payload）:
            -   store.commit('increment', 10);
        +   在大多数情况下，载荷应该是一个对象，这样可以包含多个字段并且记录的 mutation 会更易读:
            -   store.commit('increment', {  amount: 10  });
    +   对象风格的提交方式
        +   提交 mutation 的另一种方式是直接使用包含 type 属性的对象:
            -   store.commit({  type: 'increment',  amount: 10  });
        -   当使用对象风格的提交方式，整个对象都作为载荷传给 mutation 函数，因此 handler 保持不变;
    +   Mutation 需遵守 Vue 的响应规则
        +   既然 Vuex 的 store 中的状态是响应式的，
            -   那么当我们变更状态时，
            -   监视状态的 Vue 组件也会自动更新;
            +   这也意味着 Vuex 中的 mutation 也需要与使用 Vue 一样遵守一些注意事项:
                -   最好提前在你的 store 中初始化好所有所需属性。
                -   当需要在对象上添加新属性时，你应该
                -   使用 Vue.set(obj, 'newProp', 123), 
                -   或者,以新对象替换老对象: state.obj = { ...state.obj, newProp: 123 };
    +   使用常量替代 Mutation 事件类型
        +   使用常量替代 mutation 事件类型在各种 Flux 实现中是很常见的模式。
            -   这样可以使 linter 之类的工具发挥作用，
            -   同时把这些常量放在单独的文件中可以让你的代码合作者对整个 app 包含的 mutation 一目了然;
        -   '用不用常量取决于你——在需要多人协作的大型项目中，这会很有帮助。但如果你不喜欢，你完全可以不这样做。';
        +   Mutation 必须是同步函数
            -   当 mutation 触发的时候，
            -   回调函数还没有被调用，
            -   devtools 不知道什么时候回调函数实际上被调用;
            -   '实质上任何在回调函数中进行的的状态的改变都是不可追踪的';

    +   在组件中提交 Mutation
        -   可以在组件中使用 this.$store.commit('xxx') 提交 mutation，
        -   或者使用 mapMutations 辅助函数将组件中的 methods 映射为 store.commit 调用（'需要在根节点注入 store'）
        
[*Action*](https://vuex.vuejs.org/zh-cn/actions.html)
    +   Action 类似于 mutation，不同在于：
        -   Action 提交的是 mutation，而不是直接变更状态;
        -   Action 可以包含任意异步操作;
    +   Action 函数接受一个与 store 实例具有相同方法和属性的 context 对象，
        -   因此可以调用 context.commit 提交一个 mutation，
        -   或者通过 context.state 和 context.getters 来获取 state 和 getters;
    -   '实践中，我们会经常用到 ES2015 的 参数解构 来简化代码（特别是我们需要调用 commit 很多次的时候);
    +   分发 Action
        +   Action 通过 store.dispatch 方法触发：
            -   store.dispatch('increment');
        -   在 action 内部执行异步操作;
        +   Actions 支持同样的载荷方式和对象方式进行分发：
            +   以载荷形式分发:
                -   store.dispatch('incrementAsync', {  amount: 10  });
            +   以对象形式分发:
                -   store.dispatch({  type: 'incrementAsync',  amount: 10  });
            +   在组件中分发 Action
                -   你在组件中使用 this.$store.dispatch('xxx') 分发 action，
                -   或者使用 mapActions 辅助函数将组件的 methods 映射为 store.dispatch 调用（需要先在根节点注入 store）;
                
    +   组合 Action
        -   Action 通常是异步的，
        +   首先store.dispatch 可以处理被触发的 action 的处理函数返回的 Promise，
            -   并且 store.dispatch 仍旧返回 Promise;
        +   而且我们利用 async / await 这个 JavaScript 即将到来的新特性来组合 action;
        +   一个 store.dispatch 在不同模块中可以触发多个 action 函数。
            -   在这种情况下，只有当所有触发函数完成后，
            -   返回的 Promise 才会执行。

[Module](https://vuex.vuejs.org/zh-cn/modules.html)
    +   由于使用单一状态树，
        -   应用的所有状态会集中到一个比较大的对象。
        -   当应用变得非常复杂时，
        -   store 对象就有可能变得相当臃肿。
    +   为了解决以上问题，
        -   Vuex 允许我们将 store 分割成模块（module）。
        +   每个模块拥有自己的 state、mutation、action、getter、甚至是嵌套子模块——从上至下进行同样方式的分割:
            -   const moduleA = {  state: { ... },  mutations: { ... },  actions: { ... },  getters: { ... }};
            -   const moduleB = {  state: { ... },  mutations: { ... },  actions: { ... }};
            -   const store = new Vuex.Store({  modules: {    a: moduleA,    b: moduleB  }});
            -   store.state.a; /* -> moduleA 的状态 */       store.state.b; /* -> moduleB 的状态 */
    +   模块的局部状态
        -   对于模块内部的 mutation 和 getter，
        -   接收的第一个参数是模块的局部状态对象。   
    +   对于模块内部的 action，
        -   局部状态通过 context.state 暴露出来，
        -   根节点状态则为 context.rootState;
    +   对于模块内部的 getter，
        -   根节点状态会作为第三个参数暴露出来;
    +   命名空间
        +   默认情况下，
            -   模块内部的 action、mutation 和 getter 是注册在全局命名空间的,
            -   这样使得多个模块能够对同一 mutation 或 action 作出响应。
        +   如果希望你的模块具有更高的封装度和复用性，
            -   你可以通过添加 namespaced: true 的方式使其成为命名空间模块。
            -   当模块被注册后，
            -   它的所有 getter、action 及 mutation 都会自动根据模块注册的路径调整命名。
        +   启用了命名空间的 getter 和 action 会收到局部化的 getter，dispatch 和 commit;
            -   换言之，你在使用模块内容（module assets）时不需要在同一模块内额外添加空间名前缀;
            -   更改 namespaced 属性后不需要修改模块内的代码;
        +   在命名空间模块内访问全局内容（Global Assets）
            -   如果你希望使用全局 state 和 getter，rootState 和 rootGetter 会作为第三和第四参数传入 getter，
            -   也会通过 context 对象的属性传入 action。
        +   若需要在全局命名空间内分发 action 或提交 mutation，
            -   将 { root: true } 作为第三参数传给 dispatch 或 commit 即可;
        +   带命名空间的绑定函数
            -   当使用 mapState, mapGetters, mapActions 和 mapMutations 这些函数来绑定命名空间模块时，
            -   写起来可能比较繁琐;
            +   对于这种情况，
                -   你可以将模块的空间名称字符串作为第一个参数传递给上述函数，
                -   这样所有绑定都会自动将该模块作为上下文;
            +   你可以通过使用 createNamespacedHelpers创建基于某个命名空间辅助函数;
                -   它返回一个对象，
                -   对象里有新的绑定在给定命名空间值上的组件绑定辅助函数;
            +   给插件开发者的注意事项
                -   如果你开发的插件（Plugin）提供了模块并允许用户将其添加到 Vuex store，
                -   可能需要考虑模块的空间名称问题;
                -   对于这种情况，你可以通过插件的参数对象来允许用户指定空间名称;
            +   模块动态注册
                -   在 store 创建之后，
                +   你可以使用 store.registerModule 方法注册模块：
                    -   store.registerModule('myModule', {  /* ... */ })
                    -   store.registerModule(['nested', 'myModule'], {  /* ... */  })
                -   之后就可以通过 store.state.myModule 和 store.state.nested.myModule 访问模块的状态;
                +   模块动态注册功能使得其他 Vue 插件可以通过在 store 中附加新模块的方式来使用 Vuex 管理状态;
                    -   例如，vuex-router-sync 插件就是通过动态注册模块将 vue-router 和 vuex 结合在一起，
                    -   实现应用的路由状态管理;
                +   也可以使用 store.unregisterModule(moduleName) 来动态卸载模块;
                    -   注意，不能使用此方法卸载静态模块（即创建 store 时声明的模块）;
                +   在注册一个新 module 时，
                    -   你很有可能想保留过去的 state，
                    -   例如从一个服务端渲染的应用保留 state;
                    +   你可以通过 preserveState 选项将其归档：
                        -   store.registerModule('a', module, { preserveState: true })。

            +   模块重用
                +   有时我们可能需要创建一个模块的多个实例，例如：
                    -   创建多个 store，
                    +   他们公用同一个模块 
                        -   例如当 runInNewContext 选项是 false 或 'once' 时，
                        -   为了在服务端渲染中避免有状态的单例;
                    +   在一个 store 中多次注册同一个模块;
                +   如果我们使用一个纯对象来声明模块的状态，
                    -   那么这个状态对象会通过引用被共享，
                    -   导致状态对象被修改时 store 或模块间数据互相污染的问题;
                +   实际上这和 Vue 组件内的 data 是同样的问题;
                    -   因此解决办法也是相同的——使用一个函数来声明模块状态（仅 2.3.0+ 支持）;