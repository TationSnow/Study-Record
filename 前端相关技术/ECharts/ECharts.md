# ECharts

ECharts是一个使用JavaScript实现的开源可视化库，兼容性强，底层依赖矢量图形库ZRender。

https://echarts.apache.org/zh/index.html

## ECharts 快速入门

1. 引入ECharts.js文件

2. 准备一个呈现图表的盒子

   1. ```html
      <div></div>
      ```

3. 初始化ECharts实例对象

   1. ```js
      var mCharts = echarts.init(document.querySelector('div'))
      ```

4. 准备配置项

   1. ```js
      var option = {
          xAxis:{
              type: 'category', // 类目轴
              data: ['Ajax','jac','dancy']
          },
          yAxis:{
              type: 'value' // 数值轴
          },
          series:[
              {
                  name:'Language',
                  type: 'bar',
                  data:[ 70, 90, 39]
              }
          ]
      }
      ```

5. 将配置项设置给ECharts实例对象

   1. ```js
      mCharts.setOption(option)
      ```

## ECharts 相关配置项讲解

| 值     | 说明                                           |
| ------ | ---------------------------------------------- |
| xAxis  | 直角坐标系中的x轴                              |
| yAxis  | 直角坐标系中的y轴                              |
| series | 系列列表。每个系列通通过type决定自己的图表类型 |

具体更多建议查看官方文档

[Documentation - Apache ECharts](https://echarts.apache.org/zh/option.html#title)

### ECharts 通用配置

通用配置指的是任何图表都可以使用的配置

- 标题 title
- 提示 tooltip
- 工具按钮 toolbox
- 图例 legend

#### 通用配置 title

- 文本样式

```javascript
var option = {
    title:{
        text: '标题',
        textStyle:{
        	color: 'blue',
        	......
    	}
    }
}
```

- 标题边框

```js
var option = {
    title:{
        text: '标题',
        borderWidth: 5,
        borderColor: 'red',
        borderRadius: 5,
        ......
    }
}
```

- 标题位置

```js
var option = {
    title:{
        text: '标题',
        textTyle:{
        	color: 'blue',
        	left: 50,
        	top: 10,
        	......
    	}
    }
}
```



#### 通用配置 tooltip

tooltip提示框组件，用于配置鼠标滑过或者点击图表使的显示框

- 触发类型 trigger: axis / item

```js
var option = {
    title:{
        text: '标题'
    },
    tooltip:{
       	// trigger:'axis',
        trigger:'item',
    }
}
```

- 触发时机 triggerOn: mouseover / click

```js
var option = {
    title:{
        text: '标题'
    },
    tooltip:{
        // triggerOn:'mouseover',
       	triggerOn:'click',
    }
}
```

- 格式化 formatter: 字符串模板 / 回调函数

```js
var option = {
    title:{
        text: '标题',
        borderWith: 5,
        borderColor: blue,
        borderRedius: 5
    },
    tooltip:{
		// triggerOn:'mouseover',
       	triggerOn:'click',
    }
}
```





#### 通用配置 toolbox

ECharts提供的工具栏，内置有导出图片，数据视图、动态类型切换、数据区域缩放，重置五个工具

需要在toolbox下设置一个feature节点，节点中有下列属性

| 属性        | 说明             | 参数                                                         |
| ----------- | ---------------- | ------------------------------------------------------------ |
| saveAsImage | 导出图片功能     | 可以不配置参数即可具有功能                                   |
| dataView    | 查看数据视图     | 可以不配置参数即可具有功能                                   |
| restore     | 重置             | 可以不配置参数即可具有功能                                   |
| dataZoom    | 区域缩放         | 可以不配置参数即可具有功能                                   |
| magicType   | 动态切换图表类型 | 该属性下有一个type属性，存放数组，其中存放各种类型的图表，例如pie、line，这取决于你想要动态切换那些类型的图表 |



```javascript
var option = {
    title:{
        text: '标题'
    },
    tooltip:{
        // triggerOn:'mouseover',
       	triggerOn:'click',
    },
    toolbox:{
        feature:{
            saveAsImage:{},
            dataView:{},
            restore:{},
            dataZoom:{},
            magicType:{
                type: ['bar','line']
            },
        }
    }
}
```



#### 通用配置 legend

图例，用于筛选系列，需要配合series使用

- legend中的Data是一个数组
- legend中的data的值需要和series数组中某组数据的name值一致

```js
var option = {
    title:{
        text: '标题'
    },
    tooltip:{
        // triggerOn:'mouseover',
       	triggerOn:'click',
    },
    legend:{
       data:['语文','数学'], 
    }，
    series:[
        {
            name:'数学',
            type:'bar',
            data:yd1,
        },
        {
            name:'语文',
            type:'bar',
            data:yd2,
        },
    ]
}
```



### ECharts 常用图表

七大图表

1. 柱状图 bar
2. 折线图 line
3. 散点图 
4. 饼图 pie
5. 地图 
6. 雷达图
7. 仪表盘图

#### 柱状图

柱状图描述的是分类数据，呈现的是每一个分类中有多少，通过柱状图可以很清晰地看出每个分类数据的排名情况

##### 常见效果

最大值 最小值 平均值

Series下的markPoint属性与markLine

```js
var option = {
    xAxis:{
        type: 'category', // 类目轴
        data: ['Ajax','jac','dancy']
    },
    
    ......
    
    series:[
        {
            name:'Language',
            type: 'bar',
            markPoint:{
                data:[
                    {
                    	type:'max',name:'最大值'    
                    },
                    {
                        type:'min',name:'最小值'
                    }
                ]
            },
            markLine:{
                data:[
                    {
                        type:'average',name:'平均值'
                    }
                ]
            }
        }
    ]
}
```

```javascript
series:[
        {
            name:'Language',
            type: 'bar',
            markPoint:{
                data:[
                    {
                    	type:'max',name:'最大值'    
                    },
                    {
                        type:'min',name:'最小值'
                    }
                ]
            },
            markLine:{
                data:[
                    {
                        type:'average',name:'平均值'
                    }
                ]
            }
        }
```



#### 折线图

折线图适用于固定物品的每月销量等情况下的内容。

```js
var option = {
    title:{
        text: '标题'
    },
    xAxis:{
        type:'catrgory',
        data:xDataArr
    },
    yAxis:{
        type:'value'
    }
    series:[
        {
            name:'康师傅',
            type:'line',
            data:yd1,
        }
    ]
}
```



##### 常见效果

最大值、最小值、平均值（详看柱状图）、标注区间markArea

```js
var option = {
    title:{
        text: '标题'
    },
    xAxis:{
        type:'catrgory',
        data:xDataArr
    },
    yAxis:{
        type:'value'
    }
    series:[
        {
            name:'康师傅',
            type:'line',
            data:yd1,
    	    markPoint:{
                data:[
    		        {
					type:'max'
                	},
                	{
					type:'min'
                	}
                ]
            },
            markLine:{
                data:[
                   {
                    	type:'average'
                    }
                ]
            },
            markArea:{
                data:[
                    [
                        {
                            xAxis:'1月'
                        },
                        {
                            xAxis:'2月'
                        }
                    ],
                    [
                        {
                            xAxis:'7月'
                        },
                        {
                            xAxis:'8月'
                        }
                    ]
                ]
            }
        }
    ]
}
```



##### 线条控制

设置线条平滑

smooth:true

设置线条样式

 lineStyle:{
	 color:'green',
	  type:'dashed'//dotted solid
},

```js
var option = {
    title:{
        text: '标题'
    },
    xAxis:{
        type:'catrgory',
        data:xDataArr
    },
    yAxis:{
        type:'value'
    },
    series:[
        {
            name:'康师傅',
            type:'line',
            data:yd1,
    	    smooth:true,
    		lineStyle:{
    			color:'green',
                type:'dashed'//dotted solid
            },
    	    markPoint:{
                data:[
    		        {
					type:'max'
                	},
                	{
					type:'min'
                	}
                ]
            },
            markLine:{
                data:[
                   {
                    	type:'average'
                    }
                ]
            },
            markArea:{
                data:[
                    [
                        {
                            xAxis:'1月'
                        },
                        {
                            xAxis:'2月'
                        }
                    ],
                    [
                        {
                            xAxis:'7月'
                        },
                        {
                            xAxis:'8月'
                        }
                    ]
                ]
            }
        }
    ]
}
```



##### 填充风格



```js
var option = {
    title:{
        text: '标题'
    },
    xAxis:{
        type:'catrgory',
        data:xDataArr
    },
    yAxis:{
        type:'value'
    },
    series:[
        {
            name:'康师傅',
            type:'line',
            data:yd1,
    	    smooth:true,
    		lineStyle:{
    			color:'green',
                type:'dashed'//dotted solid
            },
            areaStyle: {
                color:'pink'
            }
        }
    ]
}
```



##### 紧挨边缘

boundaryGap

```js
var option = {
    title:{
        text: '标题'
    },
    xAxis:{
        type:'catrgory',
        data:xDataArr,
        boundaryGap:false
    },
    yAxis:{
        type:'value'
    },
    series:[
        {
            name:'康师傅',
            type:'line',
            data:yd1,
    	    smooth:true,
    		lineStyle:{
    			color:'green',
                type:'dashed'//dotted solid
            },
            areaStyle: {
                color:'pink'
            }
        }
    ]
}
```



##### 缩放（设置y轴起始）

当为true时，将从y轴最小那个值开始，避免了跨度过小时折线图变成直线图的情况1

```js
var option = {
    title:{
        text: '标题'
    },
    xAxis:{
        type:'catrgory',
        data:xDataArr
    },
    yAxis:{
        type:'value',
        scale:true
    },
    series:[
        {
            name:'康师傅',
            type:'line',
            data:yd1,
    	    smooth:true,
    		lineStyle:{
    			color:'green',
                type:'dashed'//dotted solid
            },
            areaStyle: {
                color:'pink'
            }
        }
    ]
}
```



##### 堆叠（在原有折线数据上进行堆叠展示）

stack:all

```js
var option = {
    title:{
        text: '标题'
    },
    xAxis:{
        type:'catrgory',
        data:xDataArr
    },
    yAxis:{
        type:'value',
        scale:true
    },
    series:[
        {
            name:'康师傅',
            type:'line',
            data:yd1,
    	    smooth:true,
    		lineStyle:{
    			color:'green',
                type:'dashed'//dotted solid
            },
            areaStyle: {
                color:'pink'
            },
            stack:'all'
        },
        {
            name:'康师傅',
            type:'line',
            data:yd1,
    	    smooth:true,
    		lineStyle:{
    			color:'green',
                type:'dashed'//dotted solid
            },
            areaStyle: {
                color:'pink'
            },
            stack:'all'
        }
    ]
}
```



#### 散点图

- 准备基本代码结构。引入js文件、DOM容器，初始化对象，设置Option
- x轴和y轴的数据，二维数组（数组1::[[身高1，体重1],[身高2，体重2],[身高3，体重3]]）
- 设置图表类型：type:scatter，xAxis和yAxis的type都要设置为value
- 调整，将坐标轴都设置为脱离0值比例，即设置scale属性

散点图可以帮助我们推断出变量间的相关性

比如身高和体重的关系

