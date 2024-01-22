<script>

//声明式渲染 vue2的写法，使得数据可以在template中使用
export default {
    data() {
        return {
            message: "h",
            user: {
                name: "user1",
                age: 18,

            },
            isActive: true,
            error:true,
            activeList:{active:true,h:true}
        }
    },
    methods: {


    },
    computed:{
        classChange:function(){
            return {
                active:this.isActive&&!this.error,
                h:this.error
            }
        }
    }
    
}

</script>

<template>
    <div>
        <!-- 1.普通使用class的方式 :放置字符串-->
        <p class="active">hello</p>
        <!-- 2.放置对象 常用-->
        <p :class="{ active: isActive, h: isActive }">hello1</p>
        <p :class="{ active: false }">hello1</p>
        <button @click="isActive = !isActive">改变isActive</button>
        <p :class="{ active: false }" class="hello2">hello1</p>
        <!-- 用对象形式 -->
        <p :class="activeList">hello1</p>



        <!-- 使用计算属性 -->
        <div :class="classChange">test</div>


        <!-- 数组语法不常用 -->
        <div :class="[message]">test</div>

        <!-- 数组+对象 -->
        <div :class="[message,{active:isActive}]">test</div>

</div>
</template>

<style scoped>
.active {
    font-size: 50px;
    color: blue;
}

.h {
    background-color: aqua;
}
</style>
