<template>
    <div>
        Old Cmp: {{ add() }}
    </div>
    <div>
        <c/>
        <cc/>
    </div>
</template>

<script lang="ts">
import {defineComponent} from "vue";
import add from "../core/add";
import C from './C.vue'
import CCCC from './CCCC.vue'

export default defineComponent({
    name: 'OldCmp.vue',
    components: {C, cc: CCCC},
    setup() {
        return {
            add
        }
    }
})
</script>

<style scoped lang="scss">

</style>
