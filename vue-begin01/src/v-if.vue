<script>
export default {
    data() {
        return {
            age:60,
            ok:false,
        }
    },
    methods: {
    },
}
</script>

<template>
    <div>
        <!-- 条件渲染 -->
        <p v-if="true">adult</p>
        <p v-if="false">not adult</p>
        <p v-if="age>=18">adult</p>
        <p v-else>not adult</p>

        <p v-if="age>=18">adult</p>
        <p v-else-if="age>=60">old</p>
        <p v-else>child</p>
    </div>
    <!-- 切换不止一个元素 template -->
    <template v-if="ok">
        <h1>Title</h1>
        <p>Paragraph 1</p>
        <p>Paragraph 2</p>
    </template>
    <template v-else>
        <h1>Title2</h1>
        <p>Paragraph 3</p>
        <p>Paragraph 4</p>
    </template>
    <button @click="ok = !ok">changeOk</button>
        <!-- 不同之处在于 v-show 会在 DOM 渲染中保留该元素；v-show 仅切换了该元素上名为 display 的 CSS 属性。 -->

</template>
