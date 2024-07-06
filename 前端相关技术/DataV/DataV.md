# DataV

组件库基于Vue （React版 (opens new window)） ，主要用于构建大屏（**全屏**）数据展示页面即**数据可视化**，具有多种类型组件可供使用：

[DataV Vue3+TS+Vite版 | DataV - Vue3](https://datav-vue3.netlify.app/Guide/Guide.html)

1pnpm install @kjgl77/datav-vue3

## 全局引入

```js
// main.ts中全局引入
import { createApp } from 'vue'
import DataVVue3 from '@kjgl77/datav-vue3'

const app = createApp(App)

app.use(DataVVue3)
app.mount('#app')
```

## 按需引入

```vue
<!-- 在.vue文件的script中import部分组件 -->
<script lang="ts" setup>
import { Decoration1, Decoration2 } from '@kjgl77/datav-vue3'
</script>
<template>
  <!-- 引入之后就可以在vue的template中直接使用 -->
  <decoration-1 :color="['pink','yellow']" style="width:200px;height:50px;" />
  <decoration-2 :reverse="true" style="width:5px;height:150px;" />
</template>
```



## 边框

