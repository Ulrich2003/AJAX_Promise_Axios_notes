# AJAX跨域解决方案：JSONP

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>原生JSONP的实现</title>
</head>
<body>
    <button id="btn">发送JSONP跨域请求</button>
</body>
<script>
    const btn = document.getElementById('btn')
    btn.onclick = function(){
        // 创建Script标签
        const script = document.createElement('script')
        // 设置Script标签的Src属性
        script.src = 'http://localhost:8000/...'
        // 将Script标签插入到文档中
        document.body.appendChild(script)
    }
</script>
</html>
```

