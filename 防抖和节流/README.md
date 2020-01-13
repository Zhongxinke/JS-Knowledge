# 防抖和节流

## 什么是防抖
以下是个人理解
> 在某个时间内，高频繁地触发时，将重新计算时间。不再触发时，按照某个时间执行。

举个栗子：

> 在等电梯的时候，当有人进入电梯时，电梯就会重新计算关门时间，第二个人进入电梯，电梯再重新计算

### 实现
```
const debounce = (fn, waitTime) => {
    let time = null
    return () => {
        clearTimeout(time)
        time = setTimeout(() => {
            fn.call(this)
        }, waitTime)
    }
}
```
### 应用场景
> 用户在输入搜索框时，调用接口时，可以使用防抖

## 什么是节流
以下时个人理解
> 减少一段时间内触发的频率

例子：
> 游戏中的冷却时间

### 实现
```
const trottle = (fn, waitTime) => {
    let isRun = false
    return () => {
        if (isRun) {
            return
        }
        isRun = true
        setTimeout(() => {
            fn.call(this)
            isRun = false
        }, waitTime)
    }
}
```