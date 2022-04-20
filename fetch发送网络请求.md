# fetch发送网络请求

```javascript
// 未优化版本
search = () => {
    fetch(`/api1/search/users?q=${value}`).then(
            response => {
                console.log('联系服务器成功了');
                return response.json()
            },
            error => {
                console.log('联系服务器失败了',error);
                return new Promise(()=>{})
            }
        ).then(
            response => {
                console.log('获取数据成功了',response);
            },
            error => {
                console.log('获取数据失败了',error);
            }
        )
}

// 优化过的版本
search = async() => {
    try{
        const response = await fetch(`/api1/search/users?q=${value}`)
        const data = await response.json()
    }catch(error){
        console.log('请求出错',error);
    }
};
```

