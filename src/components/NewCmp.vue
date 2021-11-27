<script lang="ts" setup="setup">
import add from "../core/add";
import C from './C.vue'
import CCCC from "./CCCC.vue";
import CDDD from "./DDD.vue";
import {onMounted, ref} from "vue";
import EEE from "./EEE.vue";
import EEEFFF from "./EEEFFF.vue";

const id = ref(100)
const handleChange = (n: number, d: string) => {
    console.log(d)
    id.value = n
}
const reff = ref<{
    num: number, numm: number
}>(null!)
onMounted(() => {
    console.log(reff.value.num)
    console.log(reff.value.numm)
})
</script>

<template>
    <div>
        NewCmp: {{ add() }}
    </div>
    <div>
        <c/>
    </div>
    <div>
        <c-c-c-c/>
    </div>
    <div>
        <CCCC/>
    </div>
    <div>
        <c-d-d-d :id="id" @change="handleChange" ref="reff"/>
    </div>
    <e-e-e/>
    <hr>
    <e-e-e-f-f-f/>
</template>

<style lang="scss" scoped></style>
