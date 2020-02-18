# got-knowledge
get knowlwdgw from practice usually
so come on, boy!

.QIHOO__INTERACTIVE_PLUGIN1536059088793-thumbnail {
    display: block;
    cursor: pointer;
    width: 60px;
    height: 60px;
    background: url(https://p3.ssl.qhimg.com/t01539d86c446cfd22b.png) no-repeat center;
    background-size: 100% 100%;
    -webkit-animation: tada 5s linear infinite backwards;
    -moz-animation: tada 5s linear infinite backwards;
    animation: tada 5s linear infinite backwards;  //每5S震动显示
    //animation-name: tada;
    //animation-duration: 5s;
    //animation-timing-function: linear;
    //animation-delay: 0s;
    //animation-iteration-count: infinite;
    //animation-direction: normal;
    //animation-fill-mode: backwards;
    //animation-play-state: running;
}

div
{
border:2px solid black;
outline:2px solid red;
outline-offset:15px;    //规定边框边缘之外 15 像素处的轮廓：
}

-webkit-appearance:none  //常用于在IOS下移除原生样式

vue watch 侦听器  一个比computed更通用的方法相应数据的变化   “当需要在数据变化时执行异步或者开销较大的操作”  时，使用watch。
用以监听一个声明了的属性，当其发生变化时，执行回调函数：watch:{isUserLogin(){axsio.get("...").then(data=>do some th})}}   watch中的方法func(){}相当于func:func(){}

v-if (v-else-if)* v-else  组合式条件渲染  确保再切换状态时  条件块内的事件监听器和子组件适当的被销毁和重建  与v-show不同

v-show 只是简单的设置元素的display属性  且绑定了v-show的元素始终会被渲染并保留在DOM中  不支持<templete />和<v-else>  与v-if区分

为相关组件添加一个唯一key值   使其相互独立

v-for="item in items"  用以遍历数组渲染  <ul><li v-for="item in | of items 或者 (item, index) in | of items">{{item.name}}</li></ul>  当操作数组时  Vue会检测到变化且DOM会响应式的及时渲染 ；由于 JavaScript 的限制，Vue 不能检测以下变动的数组：
	当你利用索引直接设置一个项时，例如：vm.items[indexOfItem] = newValue；
	当你修改数组的长度时，例如：vm.items.length = newLength；
以上可以用以下的方法代替：
	Vue.set(vm.items, indexOfItem, newValue)      （Vue.set === Vue.$set）;
	vm.items.splice(indexOfItem, 1, newValue)

同一标签同时使用v-for和v-if时   v-for的优先级高于v-if

事件绑定相关：
	v-on:click.stop  阻止单击事件继续传播（阻止冒泡）；
	v-on:submit.prevent  提交事件不再重载页面；
	v-on:scroll.passive   滚动事件的默认行为 (即滚动行为) 将会立即触发，尤其能够提升移动端的性能，不要把 .passive 和 .prevent 一起使用，因为 .prevent 将会被忽略，同时浏览器可能会向你展示一个警告

v-model相当于在每次输入控件的input事件时进行数据同步；v-model.lazy相当于在输入控件的change事件时进行数据同步；v-model.number返回的值为num类型的； v-model.trim去掉输入值的首尾空白字符

一个组件的data一定是一个函数   data () { return {} }  ===   data: function(){ return{} }

v-bind:visible可用于监控元素是否在页面中显示。

this.$emit("方法"，参数)   用于触发自定义函数执行

用async和await语法糖修饰的函数或者数据，是一种既是promise类型的数据，又是一般类型的数据（即既可then().then()...又可直接讀取數據）

可用this.$options.methods.方法名来相互调用methods里的方法；涉及到this指向的函数   可用 this.$options.methods.方法名.bind(this)(传参)绑定调用

vue的Props，methods,data和computed的初始化都是在beforeCreated和created之间完成的

vue传值
	1.params传参：this.$router.push({name:'parasetEdit',params:{pk_refinfo:'test',value:'test1'}});   目标页面接收参数：this.$route.params.pk_refinfo
	2.query传参： this.$router.push({path:'/uapbd/paraset/edit',query:{pk_refinfo:'test',value:'test1'}});   目标页面接收参数：this.$route.query.pk_refinfo
两种方式的区别是query传参的参数会带在url后边展示在地址栏，params传参的参数不会展示到地址栏。需要注意的是接收参数的时候是route而不是router。两种方式一一对应，名字不能混用。

在Vue生命周期的created()钩子函数进行的DOM操作一定要放在Vue.nextTick()的回调函数中，原因 是在created()钩子函数执行的时候DOM 其实并未进行任何渲染，而此时进行DOM操作无异于徒劳

$emit表示触发事件的意思？

this.$nextTick(() => {}  表示在数据变更且dom重新渲染之后  在回调中获取dom对象

vue动态绑定本地图片作为背景图时   需要用require(图片路径)引入图片

将一个对象的所有属性作为props传入一个组件的简便写法：   const object = {a:b, c:d}     v-bind='object'    等价于    a=b  c=d  即为组件的a,c   props属性赋值。

props为单向下行的绑定的属性 不能在子组件中直接改变props的值  需要先解耦  即以此props为一个data属性赋初值

vue中自定义事件最好用 my-event类型来命名而非驼峰命名法，因为会被转化为全小写导致事件的回调执行不了

".sync"修饰符： v-bind:title.sync="doc.title"  等价于 v-bind:title="doc.title"  +  v-on:update:title="doc.title"   且v-bind.sync后面不能跟表达式 （这种相当于是绑定并更新一个未赋值给data属性的一个参数的常量）   只能为一个值  如必须为表达式  则用v-model

slot插槽的作用   类似于 react的 this.props.children处理其包裹的子元素 以及相关内容   如果一个组件需要包裹其他内容   则必须用<slot></slot>声明
 <header>
    <slot name="header"></slot>                向指定卡槽插入内容  ===>>>
  </header>							 <template slot="header">
    								     <h1>Here might be a page title</h1>
  								 </template>

<component v-bind:is='组件名'></component>来切换不同的组件  避免重复渲染导致的性能问题

<keep-alive>
    <component v-bind:is='组件名'></component>     可以缓存住某一组件的状态  避免重复渲染
</keep-alive>

this.$root可以访问某一组件的根组件 且可以拿到根组件之中的data/computed/methods中的值   this.$parent可以访问到父组件

为子组件添加属性ref后   可用this.refs.<refName>来访问这个子组件  不是响应式的  不会随着某一个data值变化而变化   应避免在模板或者compted中访问使用

$on('eventName', fn) /  $off('eventName', fn) / $once('eventName', fn) 事件绑定

transition过渡组件  可以为v-if  v-show 动态组建   根节点包裹进过渡组件之中
	<transition name="fade"><p v-if="show">hello</p></transition>   自定义动画的话：可设置其name属性的值   再设置对应的name值的enter/leave等状态下的样式  <transition name="pt"><p v-if="show">hello</p></transition>    .pt-enter{...}   .pt-leave-to{...}
在css中设置进入与离开时的动画效果：.fade-enter-active, .fade-leave-active {transition: opacity .5s;}   .fade-enter, .fade-leave-to {opacity: 0;}

vue自定义指令：directives：{指令名称:{...}}    用 v-自定义指令名称    调用    // https://cn.vuejs.org/v2/guide/custom-directive.html

vue全局使用插件： 在new Vue({...})  之前 Vue.use(插件名称, {someOptions})	Vue.use会自动阻止多次注册相同插件，届时只会注册一次该插件

vue轮播组件：https://www.swiper.com.cn/api/effects/298.html    vue-awesome-swiper

Object.keys(对象名称) 返回对象的key值组成的数组

定义一个公共的全局vue实例（中央事件总线，可以绑定必要的相关子组件的事件监听器，用以在需要的地方触发）  let bus = new Vue()  在自定义公共组件中设置 基于Vue实例的相关自定义事件的触发方式 bus.on('自定义事件名称', fn)  引用时只需在main.js中注册该组件为全局组件  在需要使用的地方引入 全局公共Vue实例即可
	子组件中注册：
	mounted () {
	        bus.$on('toast', (info ,timer = 2000) => {
	          this.toastShow('default',info,timer)
	        })

	        bus.$on('success', (info ,timer = 2000) => {
	          this.toastShow('success',info,timer)
	        })

	        bus.$on('error', (info ,timer = 2000) => {
	          this.toastShow('error',info,timer)
	        })
	},
	使用：bus.$emit('toast', '该功能正在开发中，敬请期待')

在vue中使用setTimeout或者setInterval，如果按照在原来js的中方法   setTimeout(() => this.flag = true, 3000)   会发现this.flag是获取不到改变的 在es6中  应该引入setTimeout:  import { setTimeout } from "timers"  再按照原来的方法调用

使用this.$router.resolve()方法聚合路径，用于需要打开新页面跳转的情况。且用this.$router.push()无法跳转新页面；
let routeData = this.$router.resolve({ path: '/reportpreview', query: {  id: id } });
 window.open(routeData.href, '_blank');

组件化css扩展包   styled-component  https://www.styled-components.com/docs/basics   //根据设置的css相关样式生成对应的组件，可在父组件中调用

react以组件为中心代码分割以及懒加载  https://www.npmjs.com/package/react-loadable

session在不同环境下存取库    history        npm install --save history

pushState()方法  pushState({传入的参数对象}, 'title', '跳转的url（无法跨域）')  //一种改变URL却不用跳转的方法

修改 webpack 配置：   请在 config-overrrides.js 中修改，利用 react-app-rewired 这个插件，详见 https://github.com/timarney/react-app-rewired

Date.now() === new Date().getTime()    //true

window.getComputedStyle(element, pseudoElt);  获取指定元素的样式  （只读）  element为指定元素对象；pseudoElt 为指定元素的伪元素（如：after）（可选）

抛出自定义异常：throw new Error('Expected the nextReducer to be a function.')

const express = require('express');
const cors = require('cors');   //解决本地跨域问题
const app = express();
app.use(cors());

css3 filter属性
	filter: blur(10px)    [模糊处理  括号内容为模糊半径]
	filter: contrast(10%)   [对比度处理  括号内百分比为对比度的百分比]
	filter: grayScale(10%)  [灰暗度处理  括号内百分比为灰暗度的百分比]
	filter: hue-rotate(45deg / 1rad / 0.5turn)  [色相度数  括号内为色相系旋转的度数  单位可以是 度数/ rad度 / 转数]
	filter: url(图片路径)  使用图片作为滤片
	filter: brightness(50%)   亮度设置
	filter: drop-shadow(16px 16px 10px black)   设置图片边界阴影（同box-shadow）
	filter: opacity(50%)   设置透明度
	filter: saturate(200%)   设置饱和度

concat复制数组时，副本的基本类型数组项是可以任意改变的，但是其引用类型数组项改变之后，原件会随着一起改变，原因是引用类型的数组项仍然是指向原数组项的指针，可以用 {...item}  复制引用类型的数组项之后  再做更改
vue中可以用v-html将编辑好的代码插入到Dom中  eg:  var a = '<span style="color: #ff7800">啦啦</span>'   html中:  <span v-html='a'></span>

web worker: 解放主线程，Web Worker 是脱离在主线程之外的，将一些复杂的耗时的活交给它干，完成后通过 postMessage 方法告诉主线程，而主线程通过 onMessage 方法得到 Web Worker 的结果反馈；但 Web Worker 是临时的，每次做的事情的结果还不能被持久存下来，如果下次有同样的复杂操作，还得费时间的重新来一遍。Service Worker 在 Web Worker 的基础上加上了持久离线缓存能力。

vue中为标签添加v-once并为其复data的属性值为值，插值处的内容不会更新，只会渲染一次；
	利用索引直接设置一个项值时，如：this.array[2] = newValue;   正确的语法：Vue.set(vm.array, 2, newValue) 或者 this.array.splice(2, 1, newValue)    （Vue.set === vm.$set）
	修改数组的长度时，如：this.array.length = 2;   正确的语法：this.array.splice(2)
该属性值的变动不能被vue检测到,不会触发重绘

vue向props中传入Boolean类型的值   如需传入：isShow = true  直接在<Parent isShow />即可。

js class 和一般构造函数的对比：

	function Person (name, age) {
		this.age = age;
		this.name = name;
	}
	Person.prototype.sayName = function () {
		console.log(this.name);
	}
相当于用class方法构造：
	Class Person {
		constructor (name, age) {  // 用new方法实例化对象时，会自动调用constructor，未定义constructor时，会自动设置默认constructor
			this.name = name;
			this.age = age;
		}
		sayName () {
			console.log(this.name)
		}
	}

深度选择器：  在scope或者less/suss/sass中需要覆盖相关插件的自带样式  可以用   scope情况下：  >>> .demo{}选中；    less/succ/sass情况下：/deep/ .demo{}  选中

map/forEach/some/every等数组方法不会循环空数组  故 new Array(5).map(cb)不行  需要new Array(5).fill(0).map(cb)才行

使用方法： ref="usernameInput"   this.$refs.usernameInput 调用对应组件
使用 ref 属性，来为子组件分配一个引用 ID；
$refs 只会在组件渲染完成之后填充，并且它们不是响应式的；
当 ref 和 v-for 一起使用的时候，ref 获取到的是一个包含对应数据源的子组件构成的数组。

provide 选项允许我们指定，我们想要提供给后代组件的数据(data)/方法(methods)。   provide () {return {data: 1, sayData: () => {alert(data)}}}  向后代提供数据以及方法；
使用 inject 选项，来接收那些我们需要添加到当前实例中的特定属性。    inject: ['sayData']   接受父辈标签传出的属性或者方法。

使用 $on(eventName, eventHandler) 监听一个事件
使用 $once(eventName, eventHandler) 一次性地监听一个事件
使用 $off(eventName, eventHandler) 停止监听一个事件
一次性监听beforeDestory生命周期，执行picker.destory
this.$once('hook:beforeDestroy', function () {
    picker.destroy()
})
适用于实例化之后又可在某一生命周期清除：
mounted: function () {
  var picker = new Pikaday({
    field: this.$refs.input,
    format: 'YYYY-MM-DD'
  })

  this.$once('hook:beforeDestroy', function () {
    picker.destroy()
  })
}

有时你或许会有一个包含大量静态内容的组件。在这种情况下，你可以在根元素上添加 v-once 指令，来确保这些静态内容只做一次取值后就缓存起来；
在极少数的情况下，仍然需要手动强制更新，这时候你可以通过 $forceUpdate 来实现；

Vue 还允许你注册自己的自定义指令：
// 注册一个名为 `v-focus` 的【全局】自定义指令
Vue.directive('focus', {
  // 当绑定的元素插入到 DOM 时调用此函数……
  inserted: function (el) {
    // 元素调用 focus 获取焦点
    el.focus()
  }
})
//注册一个局部指令:
directives: {
  focus: {
    // 指令定义对象
    inserted: function (el) {
      el.focus()
    }
  }
}
然后在标签上使用，如：<input v-foucs />
对应的钩子函数：
bind：在指令第一次绑定到元素时调用，只会调用一次。可以在此钩子函数中，执行一次性的初始化设置。
inserted：在已绑定的元素插入到父节点时调用（只能保证父节点存在，不一定存在于 document 中）。
update：在包含指令的组件的 VNode 更新后调用，但可能之前其子组件已更新。指令的值可能更新或者还没更新，然而可以通过比较绑定的当前值和旧值，来跳过不必要的更新（参考下面的钩子函数）。
componentUpdated：在包含指令的组件的 VNode 更新后调用，并且其子组件的 VNode 已更新。
unbind：在指令从元素上解除绑定时调用，只会调用一次。
可传入的参数：
el：指令绑定的元素。可以用于直接操作 DOM。
binding：一个对象，包含以下属性：
name：指令的名称，不包括 v- 前缀。
value：向指令传入的值。例如，在 v-my-directive="1 + 1" 中，传入的值是 2。
oldValue：之前的值，只在 update 和 componentUpdated 钩子函数中可用。无论值是否发生变化，都可以使用。
expression：指令绑定的表达式(expression)，以字符串格式。例如，在 v-my-directive="1 + 1" 中，表达式是 "1 + 1"。
arg：向指令传入的参数，如果有的话。例如，在 v-my-directive:foo 中，参数是 "foo"。
modifiers：一个对象，包含修饰符，如果有的话。例如，在 v-my-directive.foo.bar 中，修饰符是 { foo: true, bar: true }。
vnode：由 Vue 编译器(Vue’s compiler)生成的虚拟 Node 节点(virtual node)。更多细节请查看 VNode API。
oldVnode：之前的虚拟 Node 节点(virtual node)，只在 update 和 componentUpdated 钩子函数中可用。

=========
module.exports=exports & require 与 export & export default & import的区别：
CommonJS模块输出是一个值的拷贝，ES6模块输出是值的引用。
CommonJS模块是运行时加载，ES6模块是编译时输出接口。
CommonJS模块无论require多少次，都只会在第一次加载时运行一次，然后保存到缓存中，下次在require，只会去从缓存取。
module.exports与exports ，是CommonJS的规范，被使用于Node.js中。export与export default ，是ES6规范，被使用于React或Vue中。
=========

Redux相关：
	1.action必须是type, payload, error, meta中的一种；
	2.按照惯例，如果error: true，payload应该是一个error对象
redux中的action仅支持原始对象，处理有副作用的action，需要使用中间件。（中间件可以在发出action，到reducer函数接受action之间，执行具有副作用的操作。）

to enable Redux Thunk, use applyMiddleware():  //用appluMiddleware()方法使用Redux Thunk   （A thunk is a function that wraps an expression to delay its evaluation.）延迟执行  执行请求等

import { createStore, applyMiddleware } from 'redux';
import thunk from 'redux-thunk';
import rootReducer from './reducers/index';

const store = createStore(
  rootReducer,   //一系列的reducers
  applyMiddleware(thunk)      //thunk使用 dispatch和getState作为参数    () =>（dispatch, getState） =>{  }
);

redux分为容器组件和展示组件   容器组件用于更改相关组件间的逻辑 数据等（一般用react-redux的connect方法 eg.    组件名称 = connect(mapStateToProps, mapDispatchToProps)(组件名称);  集中调用；  而展示组件只会根据某些组件的变化 而更改其他组件的状态（一般手动调用this.props.dispatch(reducer)）

redux部署相关顺序：1、定义相关actions以及reducers  2、根组件中createStroe（加上数据持久化persisted、路由redux（react-router-redux）等）  3、在某一组件内  分发（dispatch）相关actions（向store state中传入数据）

thunk一般用于 actions传入的数据可能作用于多个不相关的组件的情况下  即在定义actions时，可以异步请求数据之后  再将数据传入需要该数据的actions中   再在需要分发该actions的地方   this.props.dispatch()即可
	import { createStore, applyMiddleware, compose, combineReducers } from 'redux'  //redux包括cretaeStore, applyMiddleware,compose,combineReducers等方法
	import { Provider, connect } from 'react-redux'  //react-redux包括Provider标签和connect方法   connect方法用于将store的state中的数据映射到对应的组件中去  成为该组件的一个props属性(自带mapStateToProps和mapDispatchToProps)
		connect(mapStateToProps, mapDispatchToProps,或返回一个对象的任意actions/reducers函数)(对应组件)

redux/react-redux使用总结：
	1.按照不同类型、不同组件、分不同的文件，存放项目的actions和reducers，再在适当需要的地方 ，合并相关actions；
	2.开发组件时，如引用了store state中的属性值，或者dispatch了相关actions，需使用react-redux的connect方法，将相关的store state中的属性值传入该组件中；
	3.在根组件处，用redux的createStore方法以及react-redux的Provider标签  将所有的actions、reducers传入整个项目中（有需要可以使用redux-thunk增强器）；
	4.一个组件通过dispatch action改变了store state的属性值，另外一个组件可以通过mapStateToProps将对应的reducer映射成为组件的props属性再使用其改变之后的属性值（每一个reducer返回的是store state改变之后的新state，新的值）
	5.mapStateToProps单独使用时，相当于将store中state的属性值以及dispatch方法映射到组件中；但是mapDispatchToProps必须和mapStateToProps一起使用，否则找不到state中的属性值以及dispatch方法（mapDispatchToProps用于将分发action的函数映射成为组件的一个方法）
	异步actions分发器的写法：  () => (dispatch, getState) => {异步处理回调函数体}   异步action分发器 也属于action的一种   所以写在action文件中。

redux-thunk   redux-saga(dvajs)  状态机相关处理

