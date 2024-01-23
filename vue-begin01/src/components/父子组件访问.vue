<template>
    <div>
        <!-- 使用ref为组件绑定特定的id(控件上也可以使用) -->
        <Hello :aaa='123' :list="list" ref="hello"></Hello>
    </div>
    </template>
    <script>
    import Hello from './Hello.vue'
    
    export default{
        mounted(){
            console.log(this.$refs.hello.aaa);
        },
        data(){
            return {
                msg:'hello world',
                list:["yes","no"]
            }
        },
        methods:{
          
        },
    // 注册组件才能使用
        components:{
            Hello
        }
    }
    </script>
    