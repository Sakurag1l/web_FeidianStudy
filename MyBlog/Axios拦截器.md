```js
//请求拦截
import axios from 'axios'
const instance = aixos.create(){
  baseurl: '',
}
instance.interceptors.request.use(config => {
  console.log(config)
  return res          //返回请求
},err => {
  console.log(err)
})
```

## 作用：
* res中的信息不合要求
* 查看请求中的特殊信息

```js
//响应拦截
instance.intercepotors.response.use( res => {
  console.log(res);
  return res.data      //返回响应
},err => {
  console.log(err)
})
```

