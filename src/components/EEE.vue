<script lang="ts" setup="setup">
import {ref} from "vue";

const color = ref('red')
const handleChange = () => {
    if (color.value === 'red') {
        color.value = 'black'
    } else {
        color.value = 'red'
    }
}
</script>

<template>
    <div class="text">
        EEE
    </div>
    <button @click="handleChange">change color</button>
</template>

<style lang="scss" scoped>
.text {
    color: v-bind('color')
}
</style>
