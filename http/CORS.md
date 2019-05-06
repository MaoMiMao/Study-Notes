[TOC]

## Cors 

当资源从资源本身所在的服务器的**不同域**，**协议**，端口请求一个资源时、资源会发起一个跨域的HTTP请求

### [Access-Control-Allow-Origin](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Access_control_CORS#Access-Control-Allow-Origin)

```html
Access-Control-Allow-Origin: <origin> | *
**```**

origin 参数的值指定了允许访问该资源的外域 URI。对于不需要携带身份凭证的请求，服务器可以指定该字段的值为通配符，表示允许来自所有域的请求

### [Access-Control-Expose-Headers](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Access_control_CORS#Access-Control-Expose-Headers)

[`Access-Control-Expose-Headers`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Access-Control-Expose-Headers) 头让服务器把允许浏览器访问的头放入白名单

### [Access-Control-Max-Age](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Access_control_CORS#Access-Control-Max-Age) 

[`Access-Control-Max-Age`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Access-Control-Max-Age) 头指定了preflight请求的结果能够被缓存多久，请参考本文在前面提到的preflight例子。

```html
Access-Control-Max-Age: <delta-seconds>
```

### [Access-Control-Allow-Credentials](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Access_control_CORS#Access-Control-Allow-Credentials)

[`Access-Control-Allow-Credentials`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Access-Control-Allow-Credentials) 头指定了当浏览器的`credentials`设置为true时是否允许浏览器读取response的内容。当用在对preflight预检测请求的响应中时，它指定了实际的请求是否可以使用`credentials`。请注意：简单 GET 请求不会被预检；如果对此类请求的响应中不包含该字段，这个响应将被忽略掉，并且浏览器也不会将相应内容返回给网页。

### [Access-Control-Allow-Methods](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Access_control_CORS#Access-Control-Allow-Methods)

[`Access-Control-Allow-Methods`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Access-Control-Allow-Methods) 首部字段用于预检请求的响应。其指明了实际请求所允许使用的 HTTP 方法。

```html
Access-Control-Allow-Methods: <method>[, <method>]*
```

### [Access-Control-Allow-Headers](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Access_control_CORS#Access-Control-Allow-Headers)

[`Access-Control-Allow-Headers`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Access-Control-Allow-Headers) 首部字段用于预检请求的响应。其指明了实际请求中允许携带的首部字段。

```html
Access-Control-Allow-Headers: <field-name>[, <field-name>]*
```

备注：IE高互信的域名之间不遵守同源策略 ，IE未将端口加入到同源策略



**预检请求`options`**  满足下述条件则发送

> 使用了下面任一 HTTP 方法：
>
> - [`PUT`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/PUT)
> - [`DELETE`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/DELETE)
> - [`CONNECT`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/CONNECT)
> - [`OPTIONS`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/OPTIONS)
> - [`TRACE`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/TRACE)
> - [`PATCH`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Methods/PATCH)

> 人为设置了
>
> 对 CORS 安全的首部字段集合
>
> 之外的其他首部字段。该集合为：
>
> - [`Accept`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Accept)
> - [`Accept-Language`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Accept-Language)
> - [`Content-Language`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Content-Language)
> - [`Content-Type`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Content-Type) (but note the additional requirements below)
> - `DPR`
> - `Downlink`
> - `Save-Data`
> - `Viewport-Width`
> - `Width`


>  [`Content-Type`](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Content-Type)  的值不属于下列之一:
>
> - `application/x-www-form-urlencoded`
> - `multipart/form-data`
> - `text/plain`