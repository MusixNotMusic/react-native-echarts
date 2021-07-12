# 维护记录
#### 1、index.js 安卓环境问题解决 需要将tpl.html 复制到android assets 下

#### 2、toString.js 问题替换 \n换行符 %u unicode 编码问题
#### 3、renderChart.js echarts 外部参数无法进入 formatter回调中

#### [解决安卓环境问题](https://349989153.github.io/2018/04/16/native-echarts%E7%9A%84%E9%97%AE%E9%A2%98%E6%B1%87%E6%80%BB/)
#### [formatter回调问题](https://github.com/somonus/react-native-echarts/issues/175)

fork 项目从https://github.com/somonus/react-native-echarts

### 发布打包使用修改问题 (2021.07.12)
1、bug formatter时候无法 获取外部传入的 customData formater函数应该写成 [g_chartContext](https://www.shuzhiduo.com/A/A7zgln7nJ4/)
```js
    _serisesOptions.xAxis.axisLabel.formatter = function (data, index) {
					let date = new Date(g_chartContext.start + data)
					let month = date.getMonth() + 1
					month = ("0" + month).slice(-2);
					let day = date.getDate()
					day = ("0" + day).slice(-2);
					let hour = date.getHours()
					hour = ("0" + hour).slice(-2);
					let min = date.getMinutes()
					min = ("0" + min).slice(-2);
					let second = date.getSeconds()
					second = ("0" + second).slice(-2);
					// return hour + ":" + min + ":" + second
					return `${month}-${day}` + '\nn' + `${hour}:${min}:${second}`
				}
```
