# 一.前言

最近学了前端比较流行的框架vue.js和react.js，总有一种似懂非懂的感觉。借着现在还有一点印象，记一下笔记，也方便以后自己查看。正好整理一下自己最后的学习成果，把两个框架对比着来复习一下，也算是没有荒废这段时间吧。第一次写这样的笔记，写的不好，看到的朋友多提意见。* — *

# 二.vue 整理思路
Vue 是一套用于构建用户界面的渐进式框架,它易用，灵活，高效。我觉得是我最喜欢用的一种框架，相对简单，易上手，因为有数据的双向绑定这个特点，在很多地方也显得特别方便。好吧，下面讲下一我学习vue的整体思路
1.vue的安装
2.vue的指令
3.过滤器
4.计算属性和观察者
5.渲染函数
6.组件
7.组件之间的通信
8.生命周期
9.路由

 # 三 vue的安装

 安装可以分为两种方式，一种是直接利用script标签引用
 <script src="vue.js></script>
另一种方式是利用npm应用商店
npm install vue --save-dev
然后用的时候就是 import Vue from "vue";
new Vue({
    el:"#demo",//表示插入页面的id为demo之中
    data:{
        //此处为各种变量对象等
    }
    methods:{
        //此处为需要的各类方法
    }
})

 # 三 vue的指令
 指令的用法如下例子
 new Vue({
     el:"#demo",
     data:{
         name:"aa",
         html:"<span> asas</span>",
         alllist:[{
             id:0,
             name:12
         },{
             id:1,
             name:223
         }],
         bool:true
     }
 })
  1.v-text 将字符串插入标签内
 <p v-text="name"></p>
 另一种写法<p>{{name}}</p>
 比较两种写法：第二中刷新页面的时候会先{{}}再显示数据。解决办法：在标签上加v-clock

 2.v-html 将html插入页面
 <p v-html="html></p>

 3.v-for 循环(将alllist中的数据循环插入li中)
 <ul >
    <li v-for="list in alllist" v-text="list.id"></li>
 </ul>

 4.v-show 显示或者隐藏 
 <div v-show="true"></div> 为true时显示相当于display：block;为false时隐藏，相当于display:none

 5.v-if 新增或者删除
 <dis v-if="false"></div>为false时删除div节点。从页面消失。

 6.v-else (如果v-if为假则显示v-else)
 <div>
    <p v-if="false>
     隐藏
    </p>
    <p v-else>显示</p>

 </div>

 7.v-else-if
 <p v-if="name==1"></p>
<p v-else-if="name==12"></p>
<p v-else-if="name==13"></p>

8.v-bind 一般用于绑定属性和样式可简写为：
<p :style="{width:12px}"></p>
<p :class="bool?'red':'blue'"></p>

9.v-on 一般用于绑定事件 可简写为@
<button v-on:click=""> <==> <button @click=""></button>

10.v-model数据双向绑定 一般用于input select textarea
<input v-model="name" value="" type="text">
视图层改变value值时数据层的数据会改变，数据层的数据改变时同样影响视图层

、、、以下为较少用的指令
11.v-pre:在此属性的标签内不前夕{{}}
例如<p v-pre>{{name}}</p>
页面输出结果仍未{{name}}

12.v-clock:放在标签上不会再此页面先出现{{}}；

13:v-once:只会渲染一次


'''''自定义属性
Vue.directive("mycolor",{
    bind:function(el,binding){
        el.style.color=binding.value
    }
})
此时我们就可以用v-mycolor这个属性了
<p v-mycolor="blue"></p>

# 三 过滤器

