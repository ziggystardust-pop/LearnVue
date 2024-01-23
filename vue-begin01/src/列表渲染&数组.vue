<script>
export default {
    data() {
        return {
            person: ['1', '2', '3'],
            myObject: {
                title: 'How to do lists in Vue',
                author: 'Jane Doe',
                publishedAt: '2016-04-10'
            },
            testarray:[1,2,3,4,6,5,7,3]
        };
    },
    methods: {
        addperson(){
            this.person.unshift("5")
        },
        changeArray(){
            // vue2通过索引修改数组是不会响应式渲染的（vue3中可以）
            // this.testarray.push(1);//末尾添加（...省略多参数）
            // let t = this.testarray.pop();//尾部弹出
            // shift()首位删除
            // unshift()首位添加
            // reverse()翻转

            // splice()
            // （1）删除元素,第一个参数:开始删除或插入的位置下标
            // 第二个参数：要删除的个数，没有则删除后面所有元素
            
            // this.testarray.splice(0,3);
            // (2)插入,第二个参数 = 0
            // this.testarray.splice(1,0,7,8,9,100);
            // 替换元素(1,2,3位替换为7，8，9)
            // this.testarray.splice(1,3,7,8,9);
            // sort()排序,传入函数来设置排序方式
            this.testarray.sort();

        }
    },
}
</script>
<template>
    <div>
        <!-- <button @click="ok = !ok">changeOk</button> -->
        <!-- 不同之处在于 v-show 会在 DOM 渲染中保留该元素；v-show 仅切换了该元素上名为 display 的 CSS 属性。 -->
        <!-- 写不写:key="item"都可以 -->
        <!-- <ul>
            <li v-for="item in person" :key="item">
                {{ item }}
            </li>
        </ul>
        <ul>
            <li v-for="item in person">
                {{ item }}
            </li>
        </ul> -->
        <!-- v-for支持当前的索引值 -->
        <!-- <li v-for="(item, index) in person">
            {{ index }} - {{ item }}
        </li>
        <div v-for="item of person">{{ item }}</div> -->
        <!-- 使用对象 -->
        <!-- 可以通过提供第二个参数表示属性名 (例如 key)： -->
        <!-- 第三个参数表示位置索引： -->
        <!-- <li v-for="(value, key, index) in myObject">
            {{ index }}. {{ key }}: {{ value }}
        </li> -->
        <!-- key:便于vue跟踪每个节点的身份，用于重用和重新排序现有元素 -->
        <!-- key：唯一的标识 -->
        <!-- <ul>
            <li v-for="(item,key,index) in person" :key = item>
                <input type="checkbox" name="" id="">{{ item }}
            </li>
        </ul>
        <button @click="addperson">增加</button> -->




        <!-- 数组方法 -->
        <ul>
            <li v-for="item in testarray" :key="item">
                {{ item }}
            </li>
        </ul>
        <button @click="changeArray">改变数组</button>
    </div>
</template>
