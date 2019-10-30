###浏览器地址hash发生变化页面未变化

> hash模式导致

> 解决方法

1. 更改路由模式hash模式修改成history
2. 在hash模式下解决此问题 hashchange
vue工程解决此问题
```
...
mounted () {
    // 检测浏览器路由改变页面不刷新问题,hash模式的工作原理是hashchange事件
    window.addEventListener('hashchange', () => {
       let currentPath = window.location.hash.slice(1)
       if (this.$route.path !== currentPath) {
         this.$router.push(currentPath)
       }
    }, false)
}
```
