### 移动端输入框状态，收起键盘如何页面回弹

``` js
const ua = window.navigator.userAgent
document.body.addEventListener('focusout', () => {
  // 软键盘收起的事件处理
  setTimeout(() => {
    // 判断当前是否没有active element
    // 在两个Input中互相切换的时候会有bug，所以必须等所有的Input失去焦点才可以重新计算
    const activeElement = document.activeElement
    console.log(document.activeElement.tagName)
    if (activeElement !== 'INPUT' && activeElement !== 'TEXTAREA' && (ua.indexOf('iPhone') > 0 || ua.indexOf('iPad') > 0)) {
      // 键盘收齐页面空白问题
      document.body.scrollTop = document.body.scrollHeight
    }
  })
})
```
