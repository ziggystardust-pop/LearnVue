<script>

//声明式渲染 vue2的写法，使得数据可以在template中使用
export default {
    data() {
        return {
            activeColor:"red",
            fontsize:30,
            bgc:"red",
            styob:{
                color:'red',
                fontSize:'50'+'px',
                'background-color':'red'
            }
        }
    },
    methods: {


    },


}

</script>

<template>
    <div>
        <!-- 绑定内联样式1.使用字符串 -->
        <p style="color: blueviolet;">hello</p>
        <!-- 2.放置对象 font-size这种有-要改成fontSize
        或是加引号-->
        <p :style="{color:activeColor,fontSize:fontsize+'px'}">hello</p>
        <p :style="{color:activeColor,fontSize:fontsize+'px','background-color':bgc}">hello</p>
        <!--3. 样式抽取出来放入data -->
        <p :style="styob">hello</p>

<!-- 4.结合计算属性 -->

<!-- 5.数组语法 -->
<p :style="[styob,{border:'5px solid blue'}]">array</p>
 </div>
</template>
