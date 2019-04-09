### 移动端输入框状态，收起键盘如何页面回弹

```js
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
### 微信端H5页面如何实现背景音乐自动播放
```js
function autoPlayMusic() {
  if (!this.gameInfo.musicFlag) return false
     let music = document.getElementById('bg-music')
     music && music.play && music.play()
     if ( typeof WeixinJSBridge == 'object' && typeof WeixinJSBridge.invoke == 'function') {
        WeixinJSBridge.invoke('getNetworkType', {}, function(res) {
           music.play()
        })
     }
  }          
```

### 判断输入的内容中是否包含有表情
```js
function hasBrow(str){
   if(!str) return false
    var reg = /[^\u0020-\u007E\u00A0-\u00BE\u2E80-\uA4CF\uF900-\uFAFF\uFE30-\uFE4F\uFF00-\uFFEF\u0080-\u009F\u2000-\u201f\u2026\u2022\u20ac\r\n]/g
    if(str.match(reg)) return true
    return false
}
```

### 控制输入框只允许输入数字
```js
function checkNumber(event) {
  if(event.keyCode === 46 || event.keyCode === 8) return
  if(event.keyCode < 47 || event.keyCode > 58) {
      event.returnValue = false
  }
}
```
### 实现文字跑马灯效果
```js
/**
* obj1: 滚动盒子
* obj2: 滚动内容
* */
function marquee(obj1, obj2) {
    if(obj2.scrollTop + obj2.offsetHeight >= obj1.offsetHeight) {
        obj2.scrollTop = 0
    } else {
        obj2.scrollTop = obj2.scrollTop + 1
    }
}
window.clearInterval(this.timer)
this.winnerTime = window.setInterval(marquee, 100)
```

### 配置storage缓存信息读写删方法
```javascript 1.6
let storage = {
    get(key, isLocalStorage = false) {
        if (!key) return null
        let _storage = isLocalStorage ? localStorage : sessionStorage,
            props = key.split('.'),
            k = props.shift(),
            itemStr = _storage.getItem(k),
            itemObj = null
        try {
            itemObj = JSON.parse(itemStr)
            if (typeof itemObj != 'object')
                throw ('Not an object!')
        } catch (e) {
            return props.length ? null : itemStr
        }
        while (props.length && itemObj) {
            itemObj = itemObj[props.shift()]
        }
        return itemObj
    },
    set(key, value, isLocalStorage = false) {
        if (!key) return
        let _storage = isLocalStorage ? localStorage : sessionStorage,
            props = key.split('.'),
            k = props.shift()
        if (!props.length) {
            if (typeof value === 'object') value = JSON.stringify(value)
            _storage.setItem(k, value)
            return
        }
        let itemStr = _storage.getItem(k),
            itemObj = null
        if (itemStr) {
            try {
                itemObj = JSON.parse(itemStr)
                if (typeof itemObj != 'object')
                    throw ('Not an object!')
            } catch (e) {
                throw ('storage.set: key ' + k + ' 已被占用并且不是一个对象，无法为其设置属性值')
            }
        }
        let copy = itemObj = itemObj || {}
        while (props.length > 1) {
            let p = props.shift()
            copy[p] = copy[p] || {}
            copy = copy[p]
        }
        copy[props[0]] = value
        _storage.setItem(k, JSON.stringify(itemObj))
    },
    remove(key, isLocalStorage = true) {
        if (!key) return
        let _storage = isLocalStorage ? localStorage : sessionStorage
        _storage.removeItem(key)
    },
    clear(isLocalStorage = true) {
        let _storage = isLocalStorage ? localStorage : sessionStorage
        _storage.clear()
    }
}
```

### 实现数组去重的几种方式

### 实现数组对象排序的几种方式

### 手动书写防抖函数

### 手动书写节流函数

### 生成随机数的几种方式

### 手动实现bind方法

### 手动封装一个截取URL地址对象的方法

### 手动封装一个html字符串模板方法

### 手动封装一个promise

### 从url输入到页面展示之间到底发生了什么？

### 怎么实现对象的深克隆、浅克隆

### 实现本地存储有哪几种方式





