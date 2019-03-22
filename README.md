# ajax-demo
学习ajax时做的一点笔记。

#### JS如何设置HTTP请求和获取响应部分
1. http协议请求
```
GET /xxx http/1.1
Content-Type: x-www-form-url-encoded
```
2.设置第一个部分
```
request.open('GET','/xxx')
```
3.设置第二部分
```
request.setRequestHeader('yjq','18')
```
4.设置第四部分
```
request.send("username=yjq")
```


5.获取响应http状态码和状态信息

```
request.status/request.statusText
```

6.获取第二部分：响应头

```
request.getResponseHeader()
request.getAllResponseHeaders()
```


7.  获取响应体
```
request.responseText
```

---
## 仿照jQuery包装一个AJAX函数。
```
window.jQuery.ajax = function(url,method,body,success,fail){
            let request = new XMLHttpRequest()
            request.open(method,url)
            request.send(body)
            request.onreadystatechange = function(){
                if(request.readyState === 4){
                    if(request.status >=200 && request.status < 300){
                        success(request.responseText)
                    }else if(request.status >= 300){
                        let string = request.responseText
                        fail()
                    }
                }
            }
        }
```
