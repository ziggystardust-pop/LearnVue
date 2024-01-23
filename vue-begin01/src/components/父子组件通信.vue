<template>
<div>
    <h1>Content组件的内容</h1>
    <!-- 如何展示（main.js挂载的是App.vue，使用到index.html的id = 'app'控件上） -->
    <p>------------------------</p>
    <!-- 静态值可以直接传入 -->
    <!-- aaa传入数字需要:(v-bind) -->
    <!-- <Hello :message="msg" :aaa='123'></Hello> -->
    <Hello :aaa='123' :list="list"></Hello>

    <!-- <h2>{{ msg }}</h2> -->
    <p>------------------------</p>
    <button @click="msg ='你好世界'">改变msg</button>
    <!-- <Hello></Hello> -->

    <button @click="sendToApp">提交Content组件数据到App组件</button>
</div>
</template>
<!-- 将hello组件展示在content组件中 -->
<script>
import Hello from './Hello.vue'

export default{

    data(){
        return {
            msg:'hello world',
            list:["yes","no"]
        }
    },
    methods:{
        sendToApp(){
            // 触发自定义事件，通过$emit来触发事件
            // this.$emit('自定义的事件的名称','发送的事件参数')
            this.$emit('injectMsg',this.msg);

        }
    },
// 注册组件才能使用
    components:{
        Hello
    }
}
</script>
