# 前言

vue3 vuex是比较难用的，特别如果里使用ts的，pinia出来了，vue/vuex的核心维护者开发的，并且是pinia2是极其接近vuex5的提案的，pinia2会成为vue的官方状态管理器（小道消息）



# Vue3.2 Setup

B站视频：

https://www.bilibili.com/video/av209434530

https://v3.vuejs.org/api/sfc-script-setup.html#basic-syntax

https://v3.vuejs.org/api/sfc-style.html#style-scoped

## script

```vue
<script setup lang="ts">

</script>
```



### 引入文件

### 使用组件

```vue
<script lang="ts" setup="setup">
import add from "../core/add";
import C from './C.vue'
import CCCC from "./CCCC.vue";
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
</template>

<style lang="scss" scoped></style>

```

命名规则：

1、全大写

2、小写-且以-分割

默认命名：

以文件名命名

```vue
<script lang="ts">
export default {
    name: 'CDDD'
}
</script>
<script lang="ts" setup="setup">
import {ref} from 'vue';
</script>

<template>DDD</template>

<style lang="scss" scoped></style>

```



### defineProps

```vue
<script lang="ts" setup="setup">
const props = defineProps<{
    id: number
}>();

</script>
```

1、defineProps 是不需要引入

2、默认值

```vue
<script lang="ts" setup="setup">

const props = withDefaults(defineProps<{
    id?: number
}>(), {
    id: 12
})

</script>
```



### defineEmits

```vue
<script lang="ts" setup="setup">

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
</script>
```



### defineExpose

```vue
const num = ref(1212)
const numm = ref(999)

defineExpose({
    num, numm
})
```



### Typescript

```typescript
const props = defineProps<{
  foo: string
  bar?: number
}>()

const emit = defineEmits<{
  (e: 'change', id: number): void
  (e: 'update', value: string): void
}>()
```



```typescript
interface Props {
  msg?: string
  labels?: string[]
}

const props = withDefaults(defineProps<Props>(), {
  msg: 'hello',
  labels: () => ['one', 'two']
})
```



## Style



### v-bind

```vue
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

<style lang="scss" scoped>
.text {
    color: v-bind('color')
}
</style>

```



### :deep

```vue
.color .text[data-v-35852751] {
    color: green;
}
data-v-571d3f45

------

.color :deep(.text) {
    color: green;
}
===>>>
.color[data-v-35852751] .text {
    color: green;
}
```

element-plus ui框架

就会用到。



### :global

```vue
:global(body){
    background-color: #f1f1f1;
}
```



### module

```vue
<template>
  <p :class="$style.red">
    This should be red
  </p>
</template>

<style module>
.red {
  color: red;
}
</style>
```

```vue
<template>
  <p :class="classes.red">red</p>
</template>

<style module="classes">
.red {
  color: red;
}
</style>
```

