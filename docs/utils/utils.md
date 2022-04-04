# Utils

一些工具

## 将值转换为安全整数

将值转换为安全整数
使用 Math.max()和 Math.min()找到最接近的安全值。
使用 Math.round()转换为整数

```js
const toSafeInteger = (num) => Math.round(Math.max(Math.min(num, Number.MAX_SAFE_INTEGER), Number.MIN_SAFE_INTEGER))
```

## 检查两个数字是否彼此近似相等

使用 Math.abs()绝对子比较两个值的绝对差 epsilon。
epsilon 以使用默认值 0.001。

```js
const approximatelyEqual = (v1, v2, epsilon = 0.001) => Math.abs(v1 - v2) < epsilon
```

## 检查页面的浏览器选项卡是否聚焦

使用页面可见性 APIDocument.hidden 引入的属性来检查页面的浏览器选项卡是可见还是隐藏

```js
const isBrowserTabFocused = () => !document.hidden
```

## 返回一个函数(真回调，假返回)

返回一个函数，该函数接受一个参数并在它为真时运行回调，如果为假则返回它。
返回一个需要单个值 的函数 x，该函数基于 返回适当的值 pred。

```js
const when = (pred, whenTrue) => (x) => pred(x) ? whenTrue(x) : x
```

## 测量函数执行所需的时间

使用 Console.time()和 Console.timeEnd()测量开始时间和结束时间之间的差异以确定回调执行所需的时间。

```js
const timeTaken = (callback) => {
  console.time('timeTaken')
  const r = callback()
  console.timeEnd('timeTaken')
  return r
}
```

## 生成一个随机布尔值

使用 Math.random()生成一个随机数，并检查它是否大于或等于 0.5。

```js
const randomBoolean = () => Math.random() >= 0.5
```

## 检查字符串是否为大写、小写

将传递的字符串转换为大写，使用 String.prototype.toUpperCase()并将其与原始字符串进行比较。

```js
const isUpperCase = (str) => str === str.toUpperCase()
const isLowerCase = (str) => str === str.toLowerCase()
```

## 检查是否至少有一个函数返回 true

对使用||所提供的调用两个函数的结果。

```js
const either =
  (f, g) =>
  (...args) =>
    f(...args) || g(...args)
```

## num 是否在范围内

如果 num 在范围内，则返回 num。
否则，返回范围内最近的数字。

```js
const clampNumber = (num, a, b) => Math.max(Math.min(num, Math.max(a, b)), Math.min(a, b))
```

## 将给定的数字填充到指定的长度

使用 String.prototype.padStart()于垫的数目指定的长度，将其转换成字符串之后。

```js
const padNumber = (n, l) => `${n}`.padStart(l, '0')
```

## 检查是否支持触摸事件

检查中是否'ontouchstart'存在 window。

```js
const supportsTouchEvents = () => window && 'ontouchstart' in window
```

## 检查是否 sessionStorage 启用

如果所有操作成功完成，则使用 try...catch 块返回 true，false 否则返回。
使用 Storage.setItem()和 Storage.removeItem()测试存储和删除 中的值 window.sessionStorage。

```js
const isSessionStorageEnabled = () => {
  try {
    const key = `__storage__test`
    window.sessionStorage.setItem(key, null)
    window.sessionStorage.removeItem(key)
    return true
  } catch (e) {
    return false
  }
}
```

## 在指定元素的开始之前插入一个 HTML 字符串

使用 Element.insertAdjacentHTML()的位置'beforebegin'来解析 htmlString 并将其插入到 的开始之前 el。

```js
const insertBefore = (el, htmlString) => el.insertAdjacentHTML('beforebegin', htmlString)
```

## 在指定元素的结尾后插入一个 HTML 字符串

Element.insertAdjacentHTML()与位置'afterend'一起使用以解析 htmlString 并将其插入到 的结尾之后 el。

```js
const insertAfter = (el, htmlString) => el.insertAdjacentHTML('afterend', htmlString)
```

## 检查中的至少一个元件 values 被包括在 arr

使用 Array.prototype.some()和 Array.prototype.includes()检查的至少一个元素 values 被列入 arr。

```js
const includesAny = (arr, values) => values.some((v) => arr.includes(v))
```

## 检查 中的所有元素 values 是否都包含在 中 arr

使用 Array.prototype.every()和 Array.prototype.includes()检查 的所有元素是否 values 都包含在 arr.

```js
const includesAll = (arr, values) => values.every((v) => arr.includes(v))
```

## 是否在视口中可见

使用 Element.getBoundingClientRect()和 Window.inner(Width|Height)值来确定给定元素在视口中是否可见。
省略第二个参数以确定元素是否完全可见，或指定 true 以确定它是否部分可见。

```js
const elementIsVisibleInViewport = (el, partiallyVisible = false) => {
  const { top, left, bottom, right } = el.getBoundingClientRect()
  const { innerHeight, innerWidth } = window
  return partiallyVisible
    ? ((top > 0 && top < innerHeight) || (bottom > 0 && bottom < innerHeight)) && ((left > 0 && left < innerWidth) || (right > 0 && right < innerWidth))
    : top >= 0 && left >= 0 && bottom <= innerHeight && right <= innerWidth
}
```

## 返回第一个定义的非空参数

使用 Array.prototype.find()andArray.prototype.includes()查找不等于 undefinedor 的第一个值 null。

```js
const coalesce = (...args) => args.find((v) => ![undefined, null].includes(v))
```

## 克隆一个正则表达式

使用 new RegExp(),RegExp.prototype.source 和 RegExp.prototype.flags 克隆给定的正则表达式。

```js
const cloneRegExp = (regExp) => new RegExp(regExp.source, regExp.flags)
```

## 创建一个最多接受两个参数的函数，忽略任何其他参数

调用提供的函数，fn，并给出前两个参数。

```js
const binary = (fn) => (a, b) => fn(a, b)
```

## 返回第一个定义的非空参数

使用 Array.prototype.find()andArray.prototype.includes()查找不等于 undefinedor 的第一个值 null。

```js
const coalesce = (...args) => args.find((v) => ![undefined, null].includes(v))
```

## 获取当前选定的文本

如果定义了 Window.pageXOffsetand ，Window.pageYOffset 则使用 and ，否则使用 Element.scrollLeftand Element.scrollTop。
省略单个参数 ，el 以使用默认值 window。

```js
const getScrollPosition = (el = window) => ({
  x: el.pageXOffset !== undefined ? el.pageXOffset : el.scrollLeft,
  y: el.pageYOffset !== undefined ? el.pageYOffset : el.scrollTop,
})
```

## 创建一个 n 从右侧移除元素的新数组

用于 Array.prototype.slice()从右侧移除指定数量的元素。
省略最后一个参数 ，n 以使用默认值 1。

```js
const dropRight = (arr, n = 1) => arr.slice(0, -n)
dropRight([1, 2, 3]) // [1, 2]
dropRight([1, 2, 3], 2) // [1]
dropRight([1, 2, 3], 42) // []
```

## 数组唯一值

数组唯一值

```js
const uniqueElements = (arr) => [...new Set(arr)]
```

## 在给定元素上触发特定事件，可选择传递自定义数据

用于 new CustomEvent()从指定 eventType 和详细信息创建事件。
用于 EventTarget.dispatchEvent()在给定元素上触发新创建的事件。
detail 如果您不想将自定义数据传递给触发事件，请省略第三个参数。

```js
const triggerEvent = (el, eventType, detail) => el.dispatchEvent(new CustomEvent(eventType, { detail }))
```

## 过滤掉具有指定值之一的数组元素

使用 Array.prototype.includes()查找值排除。
使用 Array.prototype.filter()创建排除这些数组。

```js
const without = (arr, ...args) => arr.filter((v) => !args.includes(v))
```

## 从给定的 开始查找最接近的匹配节点 node

使用 for 循环并 Node.parentNode 从给定的 向上遍历节点树 node。
使用 Element.matches()检查，如果任何给定的元素节点相匹配的提供 selector。
如果没有找到匹配的节点，则返回 null。

```js
const findClosestMatchingNode = (node, selector) => {
  for (let n = node; n.parentNode; n = n.parentNode) if (n.matches && n.matches(selector)) return n
  return null
}
findClosestMatchingNode(document.querySelector('span'), 'body')
```

## 导出 word

使用 Blob,再用 a 标签来触发
最后用 revokeObjectURL 移除掉 createObjectURL(blob)，释放一波内存

```ts
const exportMessage = ({ fileString, fileName }): void => {
  const _fileName = `${fileName}.doc`
  const urlObject = URL || webkitURL
  //创建word格式Blob实例
  const blob = new Blob([fileString], {
    type: 'application/msword;charset=utf-8',
  })
  const link = document.createElement('a')
  link.href = urlObject.createObjectURL(blob)
  link.download = _fileName
  link.click()
  URL.revokeObjectURL(link.href) //释放内存
}
```
