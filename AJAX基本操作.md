# AJAX基本操作

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AJAX XHR代码模板</title>
</head>
<body>
    <button id="btn_get">点击发送GET请求</button>
    <button id="btn_post">点击发送POST请求</button>
    <button id="btn_fetch">使用原生fetchAPI发送AJAX请求</button>
</body>
<script>
    const btn_get = document.getElementById('btn_get')
    const btn_post = document.getElementById('btn_post')
    const btn_fetch = document.getElementById('btn_fetch')

    // GET请求
    btn_get.onclick = function(){
        const xhr = new XMLHttpRequest()
        // 响应的数据类型限定
        xhr.responseType = 'json';
        // 设置超时时间
        xhr.timeout = 2000
         xhr.ontimeout = function(){
             alert('网络超时，请稍后再试')
         }
         xhr.onerror = function(){
             alert('你的网络好像除了点问题')
         }
        //  定义请求类型和请求地址
        xhr.open('GET','http://localhost:8000/...')
        // 设置请求头
        xhr.setRequestHeader('name','ChuanyangChen')
        // 发送请求
        xhr.send()
        // 取消请求（！！注意：这句话实际开发需要删除！！）
        xhr.abort()
        xhr.onreadystatechange = function(){
            if(xhr.readyState === 4){
                if(xhr.status >= 200 && xhr.status<300){
                    // 响应行
                    console.log(xhr.status)
                    console.log(xhr.statusText)
                    // 响应头
                    console.log(xhr.getAllResponseHeaders());
                    // 响应体 (重要)
                    console.log(xhr.response);
                }
            }
        }
    }

    // Post请求
    btn_post.onclick = function(){
        const xhr = new XMLHttpRequest();
        // 响应的数据类型限定
        xhr.responseType = 'json';
        // 设置超时时间
        xhr.timeout = 2000
         xhr.ontimeout = function(){
             alert('网络超时，请稍后再试')
         }
         xhr.onerror = function(){
             alert('你的网络好像除了点问题')
         }
        xhr.open('POST','http://localhost:8000/...')
        // 设置请求头
        xhr.setRequestHeader('name','ChuanyangChen')
        // send中的内容放入请求体
        xhr.send('a=100&b=200&c=300');
        // 取消请求（！！注意：这句话实际开发需要删除！！）
        xhr.abort()
        xhr.onreadystatechange = function(){
            if(xhr.readyState === 4){
                if(xhr.status>=200 && xhr.status<300){
                    console.log(xhr.response); 
                }
            }
        }
    }

    // fetch发送AJAX请求
    btn_fetch = function(){
        fetch('http://localhost:8000/...?vip=10',{
            // 请求方法
            method:'POST',
            // 请求头
            headers:{
                name:"chuanyangChen"
            },
            // 请求体
            body:'username=admin&password=admin'
        }).then(response=>{
            console.log(response)
        })
    }
</script>
</html>
```

