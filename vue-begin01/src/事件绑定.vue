<script>
export default {
    data() {
        return {
            counter: 0
        };
    },
    methods: {
        // addCounter(){
        //     this.counter++;
        // },
        addCounter(e) {
            // this.counter++;
            //事件对象e
            console.log(e);//点击h2时会传入点击事件
        },
        plusnumber(num, e) {
            this.counter += num;
            // console.log(e);
        },
        buttonClick() {
            console.log("子元素");
        },
        divClick() {
            console.log("父元素");

        },
        submitClick() {
            console.log("sub click");
        },
        onceClick() {
            console.log("触发一次");
        },
        keyUpTest() {
            console.log("键盘被按下，提交");
        }
    },
}
</script>
<template>
    <div>
        <!-- (1)绑定事件通过函数处理 -->
        <h2 @click="addCounter">{{ counter }}</h2>

        <!-- 绑定事件（2）通过JavaScript代码处理 -->
        <h2 @click="counter++">{{ counter }}</h2>
        <!-- (3) 传递参数 -->
        <h2 @click="plusnumber(10)">{{ counter }}</h2>
        <!-- 既有事件对象（作为实参传入）又传递参数 -->
        <h2 @click="plusnumber(10, $event)">{{ counter }}</h2>
        <!-- 一个点击触发多个函数 ,需要加()，事件参数也要传入-->
        <h2 @click="plusnumber(10, $event), addCounter($event)">{{ counter }}</h2>
        <!-- 阻止事件冒泡(执行完自身的事件还会执行父元素的事件) .stop-->
        <div @click="divClick">
            <button @click.stop="buttonClick">事件冒泡</button>
        </div>
        <!-- 阻止默认行为(prevent)，下面例子的默认行为是submit点击，form就会提交
        表单提交： 当用户点击提交按钮时，表单将提交。
        如果没有指定 action 属性，表单将提交到当前页面的 URL。
        页面刷新： 默认情况下，表单提交后会导致整个页面重新加载。
        这是因为浏览器将执行提交操作，将表单数据发送到服务器，然后接收并处理来自服务器的响应。
        如果没有 JavaScript 干预，页面将按照提交后的响应重新加载。
        -->
        <form action="">
            <input type="submit" @click.prevent="submitClick">
        </form>
      <!-- .once,只触发一次回调 -->
        <button style="background-color:antiquewhite;" @click.once="onceClick">事件冒泡</button>
        <!-- 键盘修饰符 .{keyCode(键盘编码) | keyAlias（简写）}监听键盘的某个键帽-->
        <input type="text" @keyup="keyUpTest">
        <!-- 限制按键 enter抬起才调用函数
                .enter
                .tab
                .delete (捕获“Delete”和“Backspace”两个按键)
                .esc
                .space
                .up
                .down
                .left
                .right
    -->
        <input type="text" @keyup.enter="keyUpTest">

    </div>
</template>
