<script>
import Content from './components/Content.vue'
export default {
    components: {
        Content,
    },
    data() {
        return {}
    },
    methods: {
        getContentMsg(value) {
            //此函数的默认参数即为
            // 子组件传来的数据
            console.log(value);
        }
    },
}
</script>
<template>
    <!-- 在template中使用组件展示Content -->
    <div>
        <!-- 子组件中点击按钮触发了injectMsg事件，触发父组件中的getContentMsg函数 -->

        <!-- 插槽必须使用双标签语法，填进去的东西会自动替换插槽 -->
        <Content>
            <!-- vue2: -->
            <!-- <template><button slot="a">按钮a</button></template> -->
            <!-- vue3:  -->
            <template v-slot:a><button>按钮a</button></template>
            <template v-slot:b><button>按钮b</button></template>
        </Content>

        <!-- <Content></Content> -->
        <!-- <Content></Content> -->
        <!-- 通过v-on监听子组件中的自定义事件 -->


        <!-- 无序列表 -->
        <Content>
            <!-- 结合v-for -->
            <template v-slot:default="slotProps">
                <ul>
                    <li v-for="item in slotProps.list" :key="item">
                        {{ item }}
                    </li>
                </ul>
            </template>
        </Content>
        <!-- 有序列表 -->
        <Content>
            <!-- 结合v-for -->
            <template v-slot:default="slotProps">
                <ol>
                    <li v-for="item in slotProps.list" :key="item">
                        {{ item }}
                    </li>
                </ol>
            </template>

        </Content>

    </div>
</template>
