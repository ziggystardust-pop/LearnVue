<script>

//声明式渲染 vue2的写法，使得数据可以在template中使用
export default{
  data(){
    return{
     message:"hello worldddd",
     user:{name:"user1",
     age:18,

    },

  }},
  methods:{
    changeMessage(){
        this.message = "new message";
    },
    test(){
        return this.message.split('').reverse().join(''); 
    }
  },
  computed:{
    reverseMsg:{
        get(){
        return this.message.split('').reverse().join('');
    },
        set(newvalue){
            this.message = newvalue;
    }
    }  
    
    },
    now() {
    return Date.now()
  },
    watch:{//监听数据的变化,message改变则执行对应的函数
        message:{
            immediate:true,//初始化就调用监听函数
            handler:function(newvalue,oldValue){
                console.log("new",newvalue);
            console.log(oldValue);
            //执行异步操作，或复杂的逻辑
//一个数据影响多个数据
            if(newvalue.length<5||newvalue.length>10){
                console.log("输入框内容长度不能小于5或大于10");
            }
            }
        },
        // user:{
        //     handler:function(newvalue){
        //     console.log(newvalue);
        //     console.log(newvalue.name);
        // },
        // deep:true//一层层向下遍历

        // }
        //如何只监听user.name:使用字符串优化
        "user.name":{
            handler:function(newvalue){
            console.log(newvalue);
            // console.log(newvalue.name);
        },
        deep:true//一层层向下遍历

        }
        
        
    }
  }
  
</script>

<template>
 
<div>
    <!-- 直接调用方法，不需要() -->
    <!-- 只要依赖值不变就不会重新计算 -->
    <p>{{ reverseMsg }}</p>
    <p>{{ test() }}</p>
    <p>{{ now }}</p>
    <button @click="changeMessage">改变message</button>
<!-- 自动调用set函数 -->
    <button @click="reverseMsg='你好'">改变reverseMsg</button>
    <!-- 数据双向绑定 -->
<input type="text" v-model="message">

<p>{{ user.name }}</p>

<button @click="user.name='newuser'">改变名字</button>






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
