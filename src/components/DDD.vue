<script lang="ts">
export default {
    name: 'CDDD'
}
</script>
<script lang="ts" setup="setup">

import {ref} from "vue";

const props = withDefaults(defineProps<{
    id?: number
}>(), {
    id: 12
})
const emits = defineEmits<{
    (e: 'change', n: number, d: string): void
}>()
const handleClick = () => {
    emits('change', 12, "fds")
}
const num = ref(1212)
const numm = ref(999)

defineExpose({
    num, numm
})
</script>

<template>
    <h3>DDD</h3>
    <div>
        id: {{ props.id }}
    </div>
    <div>
        <button @click="handleClick">父组件你把id改一下</button>
    </div>
</template>

<style lang="scss" scoped></style>
