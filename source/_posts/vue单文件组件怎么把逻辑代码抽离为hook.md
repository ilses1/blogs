---
title: vue单文件组件怎么把逻辑代码抽离为hook
date: 2023-09-27 14:46:58
categories:
 - vue
tags:
 - 组件拆分
---
---
theme: smartblue
---
## 普通的vue单文件组件
log.vue

```js
<script setup lang="ts">
import { ref } from 'vue';

const index = ref<number>(1)
</script>

<template>
    <h1>{{ index }}</h1>
</template>

<style scoped>
h1 {
    color: red;
    font-size: 50px;
}
</style>
```
## 需求
- 1.把js逻辑代码抽离出去<br>

[具体问题链接,前情提要](https://juejin.cn/post/7273141970057494565)


## 具体实现
### log.hook.ts

```js
import { ref } from "vue";

export function uselogHook() {
    const index = ref<number>(1);
    
    return {
        index
    }
}
```

### log.vue

```js
<script setup lang="ts">
import { uselogHook } from "./log.hook";

const { index } = uselogHook()
</script>

<template>
    <h1>{{ index }}</h1>
</template>

<style scoped>
h1 {
    color: red;
    font-size: 50px;
}
</style>

```

## 增加需求


- 1.有一个comoms.ts的文件,其中有一些公共的工具方法暴露出一个类,导入hook在组件中使用

- 2.props和emits传入hook使用

- 3.hook中使用生命周期,进行增加监听和移除监听

### comoms.ts如下
```js
export default class Commons {
    constructor() {
    }

    formatTime() {
        console.log('formatTime');
        return new Date().toLocaleString();
    }

}
```
### log.hook.ts

```js
import { onBeforeUnmount, onMounted, ref } from "vue";
// 导入common.ts
import commonHook from "../common";
export interface Props {
    name: string
}
export interface Emits {
    (e: 'close'): void
}
export function uselogHook(props: Props, emits: Emits) {
    const _props = props
    const _emits = emits
    // 实例化common类
    const common = new commonHook();
    const index = ref<number>(1);
    // 使用传入的参数
    const click = () => {
        console.log(_props.name);
    }

    const keydown = () => {
        console.log("keydown");
        _emits("close");
    }
    onMounted(() => {
        document.addEventListener("keydown", keydown);
    })
    onBeforeUnmount(() => {
        document.removeEventListener("keydown", keydown);
    })

    // 返回变量方法和common实例
    return {
        index, click, keydown, common
    }
}
```
### log.vue

```js
<script setup lang="ts">
// 导入hook和props,emits类型
import { uselogHook, Props, Emits } from "./log.hook";

// 初始化props,emits
const props = withDefaults(defineProps<Props>(), {
    name: 'default'
})
const emits = defineEmits<Emits>()

// 使用hook传入props,emits  结构出index,click,common
const { index, click, common } = uselogHook(props, emits)
</script>

<template>
    <!-- 显示内容 -->
    <h1 @click="click">{{ index }}</h1>
    <!-- 使用 common公共方法-->
    <h1>{{ common.formatTime() }}</h1>
</template>

<style scoped>
h1 {
    color: red;
    font-size: 50px;
}
</style>

```

