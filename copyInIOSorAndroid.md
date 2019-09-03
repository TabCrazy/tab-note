## 兼容Android 与 IOS 移动web站点 点击按钮复制方案
```
function copy(message) {
        var input = document.createElement("input");
            input.value = message;
            document.body.appendChild(input);
            input.select();
            input.setSelectionRange(0, input.value.length), document.execCommand('Copy');
            document.body.removeChild(input);
            console.log("复制成功", "text");
}
```
