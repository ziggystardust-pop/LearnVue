<script>

//声明式渲染 vue2的写法，使得数据可以在template中使用
export default{
  data(){
    return{
      name:"test",
      num:0,
      message:"<h2>message</h2>",
      id:"id1",
      url: 'https://m.360buyimg.com/babel/jfs/t1/112553/14/1554/195759/5e994b63E9fdca944/e23f1f8570903d10.jpg',
      att:'id2'
    }
  },
  methods:{
    changeName:function(){
      this.name = 'user';
    },
    change(){
      this.id = "id";
    }
  }
}
</script>

<template>
  {{ name }}
  {{ num }}
  <div>
    
    <span v-once>{{ name }}</span>
    <!-- 点击改变名字v-once修饰的地方不会更新 -->
    <button @click="changeName">改变名字</button>
  
    <!-- {{  }}展示html代码需要特殊处理 -->
  <p v-html="message"></p>



  <!-- v-bind动态绑定属性内容 -->
  <!-- <p v-bind:id = "id">v-bind</p>
  <img v-bind:src="url" alt="test">
  <p :id="id">v-bind</p> -->


  <!-- 用函数 -->
  <!-- <button @click="change">改变颜色1</button> -->
  <!-- 用js表达式 -->
<!-- <button @click="id='id2'">改变颜色2</button>
<p>{{ num+=1 }}</p>
<p>{{ name.split('').reverse().join('') }}</p> -->

<button v-on="click"></button>
<!-- v-on语法糖：@ -->



<!-- 动态参数 -->
<!-- 动态属性 -->
<p v-bind:[att]= "id">v-bind</p>


<!-- 动态事件 -->
<button @[MouseEvent]="att='class'"></button>
</div>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
#id2{
  color: aqua;
}
</style>
