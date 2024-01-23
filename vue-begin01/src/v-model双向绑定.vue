<script>
export default {
    data() {
        return {
            msg:"hello",
            checked:true,
            fruit:[],
            sex:'man',
            city:null,
            citys:[],
            citys2:[],
            test:"beijing",
            age:null
        }
    },
    methods: {
        change(e){
            this.msg = e.target.value;
        },
        changecity(){
            this.test = "shaghai";
        }
    },
}
</script>

<template>
    <div>
<!-- 关联到data中的msg，输入框修改则msg关联修改 双向绑定-->
<!-- 原理：
1. v-bind绑定一个value属性
2. v-on给当前元素添加一个input事件
-->
        <!-- <input type="text" v-model="msg"> -->
        {{ msg }}
<!-- v-bind是单方面的绑定，没有触发input事件 -->
        <input type="text" v-bind:value="msg" @input="change">

        <!-- v-model表单基础用法 -->
        <!-- 复选框 
        为单个时就是boolean值,勾选v-model自动赋值checked为true        
    -->
        <input type="checkbox" v-model="checked">

        {{ checked }}
        <!-- 复选，多个勾选框 -->
        <!-- 绑定value值 ，点击后添加到数组-->
        <input type="checkbox" v-model="fruit" value="苹果">苹果
        <input type="checkbox" v-model="fruit" value="香蕉">香蕉
        <input type="checkbox" v-model="fruit" value="火龙果">火龙果
        <h1>喜欢的水果：{{ fruit }}</h1>

        <!-- 单选radio 
        javascript:加name='sex'
        -->
        <input type="radio" v-model="sex" value="man">man
        <input type="radio" v-model="sex" value="woman">woman
        <h1>{{ sex }}</h1>
        <!-- 下拉选项，选中某个后将其value值赋值给v-model绑定的变量
        可以在data中给默认值 -->
        <select name="" id="" v-model="city">
            <option value="">--Please choose an option--</option>
            <option value="new york">new york</option>
            <option value="tokyo">tokyo</option>
        </select>
        <h1>{{ city }}</h1>
        <!-- 多选 -->
        <select name="" id="" v-model="citys" multiple>
            <option value="">--Please choose an option--</option>
            <option value="new york">new york</option>
            <option value="tokyo">tokyo</option>
        </select>
        <h1>{{ citys }}</h1>

        <!-- 值绑定 -->
        <select name="" id="" v-model="citys2" multiple>
            <option value="">--Please choose an option--</option>
            <option :value="test">{{ test }}</option>
        </select>
        <h1>{{ citys2 }}</h1>
        <button @click="changecity">改变多选中的城市</button>
        <br>
        <!-- 修饰符 (1).lazy 转为在change事件后同步数据
        输入框失去焦点再同步输入框的数据
        
        -->
        <input type="text" v-model.lazy="msg">
        {{ msg }}<br>
        <!-- .number -->
        <input v-model.number="age" type="text">
        {{ age }}<br>
        <!-- .trim -->
        <input v-model.trim="msg" />
        {{ msg }}
</div>
</template>
