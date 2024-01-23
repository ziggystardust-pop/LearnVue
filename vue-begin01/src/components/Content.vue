<template>
    <div>
        <h2>content组件内容</h2>
        <div>
            <slot name="a"></slot>
            
            <slot name="b"></slot>
            <!-- 插槽prop -->
            <!-- (1)子组件通过v-bind绑定list -->
            <slot :list="list"></slot>

        </div>
    </div>
</template>
<script>

export default {

    data() {
        return {
            list:[1,2,3,2,5]
        }
    },
    methods: {

    },
   
}
</script>
    