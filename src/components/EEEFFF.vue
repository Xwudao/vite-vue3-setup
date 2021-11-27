<script lang="ts" setup="setup">
import {ref} from 'vue';
import EEE from "./EEE.vue";
</script>

<template>
    <div class="color">
        <e-e-e/>
        <span :class="$style.color">NNM</span>
    </div>
</template>
<!--
react-js

css-in-js

module
styled-component

知乎比喻：vue 自动挡的车
react 手动挡


//渐进式框架， vue3
vue的官方，把一切都给你准备好了，《并且都还是最佳实践》，大部分场景都不会出现什么大的问题。

react，react的官方的定义，ui 视图层的框架，你什么router , state, style 全不管， 你社区自己折腾吧

-->

<style lang="scss" scoped module>
//.color {
//    .text {
//        color: green;
//    }
//}

.color :deep(.text) {
    color: green;
}

:global(body) {
    background-color: #f1f1f1;
}
</style>
