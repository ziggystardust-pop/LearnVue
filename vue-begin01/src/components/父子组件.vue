<template>
    <div>
        <p>hello</p>
        <h2>{{ message }}</h2>
        <h2>{{ aaa }}</h2>
        <h2>{{ typeof aaa }}</h2>
        <h2>{{ list }}</h2>
        
    </div>
</template>
<script>
    export default{
        // 在组件的 props 列表上声明要传来的属性的名字
        // props:['message','aaa']
        // props类型限制
        props:{
            message:{
                type:String,
                default:"okok",
                // required:true//必须传入
            },
            aaa:Number,
            //接收传入的数组,默认值略有不同,对象和数字的默认值需要一个函数来返回
            list:{
                type:Array,
                default(){
                    return []
                }
            }
        },
        mounted(){
            // 子组件先执行
            console.log(this.$parent);
            console.log(this.$root);
        }
    }
</script>