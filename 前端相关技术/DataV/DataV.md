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

## 布局方式

### Flex 布局

设置为flex布局的父元素称为容器，其内部的各个标签被称为项目

```html
<style>
    div {
        display:flex;
    }
</style>
```

#### 容器的属性

##### flex-direction属性：更改方向是垂直还是水平

- 作用：设置主轴的方向，即决定了Flex容器中的子元素（Flex items）的排列方式。

- 值：	
   - `row`（默认值）：主轴为水平方向，子元素从左到右排列。
   - `row-reverse`：主轴为水平方向，子元素从右到左排列。
   - `column`：主轴为垂直方向，子元素从上到下排列。
   - `column-reverse`：主轴为垂直方向，子元素从下到上排列。



##### justify-content属性：更改对其方式

- **flex-start**：默认值。项目被放置在容器的起始位置。如果主轴是水平方向，则项目被放置在容器的左端。
- **flex-end**：项目被放置在容器的结束位置。如果主轴是水平方向，则项目被放置在容器的右端。
- **center**：项目在容器中居中对齐。
- **space-between**：项目之间的间隔相等，第一个项目位于容器的起始位置，最后一个项目位于容器的结束位置。
- **space-around**：项目两侧的间隔相等。因此，项目之间的间隔比项目与容器边界的间隔大一倍。
- **space-evenly**：所有项目之间的间隔（包括项目与容器边界的间隔）都相等



##### align-content属性：



##### align-items属性：





##### flex-wrap属性：

- 作用：设置子元素是否换行。

- 值：

  - `nowrap`（默认值）：子元素不会换行，即使容器的空间不足以容纳它们。所有子项都将排列在一行（或一列，取决于 `flex-direction` 的值），即使这会导致一些子项被挤压或溢出容器。适用于子项数量较少，且你希望它们全部保持在同一行（或列）中的场景。这可能会导致某些子项尺寸被压缩以适应容器大小，或者在某些情况下，子项可能会溢出容器。

  - `wrap`：如果容器的空间不足以容纳所有子元素，则子元素会换行到下一行。如果子项的总宽度（或高度，取决于主轴方向）超过了容器的宽度（或高度），则子项将换行到新的一行（或列）继续排列。这是最常见的用法之一，特别是当你不确定子项数量或它们的大小可能会变化时。使用 `wrap` 可以确保所有子项都能被显示，并且当它们无法全部容纳在一行（或列）中时，会自动换行到下一行（或列）。
  - `wrap-reverse`：与`wrap`类似，但子元素的排列顺序与`wrap`相反，从底部开始向上换行。



##### flex-flow属性：

- 作用：`flex-direction`和`flex-wrap`属性的简写形式，默认值为`row nowrap`。
- 值：可以是`flex-direction`和`flex-wrap`的任意组合，如`row wrap`、`column nowrap`等。







#### 项目的属性

##### flex 属性

语法：flex : [是否沿着主轴方向自动撑开：0 否 1 是] [空间不足时该项目是否自动缩小 0否 1是] [设置占用空间比例或固定大小的位置]

```html
<style>
    *{
        flex: 0 0 auto;
    }
</style>
```

##### order属性





### Grid 网格布局

- Flex布局是一维布局，主要用于控制元素在行或列方向上的排布，虽然可以通过改变主轴方向来实现一定程度的二维布局效果，但本质上仍是以一维为主。
- Grid布局是二维布局，可以同时控制元素在行和列方向上的排布，具有更高的灵活性和控制力。

- Flex布局更适合用于局部布局，如导航栏、侧边栏等组件的布局，以及在小屏幕设备上的响应式布局。
- Grid布局则更适合用于整个页面的规划，能够更精确地控制页面各个部分的位置和大小。

```html
<style>


  .container{
    display: grid;
      /* 三列 每列各自一等分 既全体列三等分*/
      /* 三行 每行各自一等分 既全体行三等分*/
    grid-template-columns: repeat(3,1fr);
    grid-template-rows: repeat(3,1fr);
  }
    

</style>
```



#### 跨行与跨列处理

语法：

```scss
// 父容器设置为grid模式 
// 此处为9x9的表格阵列
.container{
    display: grid;
    // repeat() 函数重复9次 每列每行各1等分
    grid-template-columns: repeat(9,1fr);
    grid-template-rows: repeat(9,1fr);
    // 使用此模式代表 
    // 创建五列 大小分别为 1 1 4 1 1 等分
    // 创建五行 大小分别为 1 1 1 1 1 等分
    // grid-template-columns: 1fr 1fr 4fr 1fr 1fr;
    // grid-template-rows: 1fr 1fr 1fr 1fr 1fr; 
    gap: 10px;

    .item {
      padding: 20px;  
      color:white;
    }

    // 给编号为32的项目添加test1类名
	// 此时column 5表示其在第五列 向右合并 8-5=3列（包含本身），结果为合并三格为一格
    // 此时row 4表示其在第四行 向下合并 9-4=5行（包括本身），结果为向下合并五格为一格
    .test1 {
      grid-column: 5/8; 
      grid-row: 4/9;
      background: #000;
    }

  }
```







## 边框

语法：

```html
<dv-border-box1>
</dv-border-box1>

<dv-border-box2>
</dv-border-box2>

...

<dv-border-box13>
</dv-border-box13>
```

### 属性

| 属性             | 作用             | 接受参数                                 | 示例                               | 备注       |
| ---------------- | ---------------- | ---------------------------------------- | ---------------------------------- | ---------- |
| color            | 修改边框颜色     | 数组，支持十六进制、颜色、rgba等的数组。 | :color="['#fff000','#000fff']"     | 所有       |
| background-color | 边框的背景颜色   | 颜色值，支持十六进制、颜色、rgba等。     | background-color="rgba(0,0,0,0.2)" | 所有       |
| title            | 边框标题         | 文本，                                   | title="数据大屏"                   | 边框11特有 |
| title-width      | 边框标题背景宽度 | 数值，                                   | :title-width="350"                 | 边框11特有 |
|                  |                  |                                          |                                    | 边框11特有 |



## 装饰





### 属性

| 属性  | 作用         | 接受参数                                 | 示例                           | 备注 |
| ----- | ------------ | ---------------------------------------- | ------------------------------ | ---- |
| color | 修改装饰颜色 | 数组，支持十六进制、颜色、rgba等的数组。 | :color="['#fff000','#000fff']" | 所有 |
|       |              |                                          |                                |      |
|       |              |                                          |                                |      |
|       |              |                                          |                                |      |
|       |              |                                          |                                |      |



## 按钮

语法：

```html
<dv-button @click="console.log('click')" border="Border3" color="#c8161d" font-color="#e18a3b">智慧水利</dv-button>
```

### 属性

| 参数      | 说明         | 可选值                                                       | 默认值            |
| --------- | ------------ | ------------------------------------------------------------ | ----------------- |
| color     | 主题颜色     | -                                                            | \#2058c7          |
| fontColor | 字体颜色     | -                                                            | 默认和 color 相同 |
| fontSize  | 字体大小     | -                                                            | 14                |
| bg        | 是否显示背景 | true / false                                                 | true              |
| border    | 边框类型     | Border1 到 Border6, 也可以传入自己的 svg 组件或 datav 的边框组件 | Border1           |

## 图表

### 胶囊柱图表

#### 语法

```html
<dv-capsule-chart :config="config" />
```

```vue
<template>
	 <dv-capsule-chart :config="config" style="width:25rem;height:15rem" />
</template>


<script setup>
const config = reactive({
  data: [
    {
      name: '南阳',
      value: 167
    },
    {
      name: '周口',
      value: 123
    },
    {
      name: '漯河',
      value: 98
    },
    {
      name: '郑州',
      value: 75
    },
    {
      name: '西峡',
      value: 66
    },
  ],
  colors: ['#e062ae', '#fb7293', '#e690d1', '#32c5e9', '#96bfff'],
  unit: '万元',
  labelNum: 8,
})
</script>

<style>

</style>
```

#### 属性信息

|      属性      |     说明     |      类型       |  可选值  | 默认值 |
| :------------: | :----------: | :-------------: | :------: | :----: |
|      data      |    柱数据    | `Array<Object>` | data属性 |  `[]`  |
|      unit      |     单位     |     String      |   ---    |  `''`  |
|     colors     |    环颜色    | `Array<String>` |  `[1]`   | `[2]`  |
|   showValue    |   显示数值   |     Boolean     |   ---    | false  |
| textColor1.4.0 |   文字颜色   |     String      |   ---    | '#fff' |
| fontSize1.4.0  |   文字大小   |     Number      |   ---    |   12   |
| labelNum1.7.2  | 标签显示数量 |     Number      |   ---    |   6    |

### 水位图图表

#### 语法

```html
<dv-water-level-pond :config="config"/>
```





### 飞线图图表



## 其他











## 背景图像

添加背景图像

```vue
<template>
<div class="content bg">
</div>
</template>

<style scoped>
.bg{
    background: url(../../assets/background/bg1.jpg);
    background-size: cover;
}
.content{
    width: 100%;
    /* height: 100vh; */
    height: 88vh;
    color: #d3d3d3;
}
</style>

<script>

</script>
```





## 全屏容器

数据可视化页面一般在浏览器中进行全屏展示，全屏容器将根据屏幕比例及当前浏览器窗口大小，自动进行缩放处理。浏览器全屏后，全屏容器将充满屏幕。

建议在全屏容器内使用百分比搭配flex进行布局，以便于在不同的分辨率下得到较为一致的展示效果。

使用前请注意将`body`的`margin`设为0，否则会引起计算误差，全屏后不能完全充满屏幕

