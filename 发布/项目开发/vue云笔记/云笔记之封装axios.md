### 前提

因为axios根据请求方法不同，传递的参数也有所不同，所以需要二次封装，来统一参数，增加复用性。


### 实现

```ts
import axios from 'axios'

axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded'

  
axios.defaults.baseURL = 'https://note-server.hunger-valley.com'

  
axios.defaults.withCredentials = true

  

interface Options {

 url: string

 method: string

 validateStatus: (value: number) => boolean

 data?: {}

 params?: {}

}

```



```ts
export default function request(url: string, type = 'GET', data = {}) {
  return new Promise((resolve, reject) => {
    const option: Options = {
      url,
      method: type,
      validateStatus(status: number) {
        window.console.log(status)
        return (status === 400 || (status >= 200 && status < 300))
      },
    }
    if (type.toLowerCase() === 'get') { option.params = data }

    else {
      option.data = data
      window.console.log(option)
    }

    axios(option).then((res) => {
      if (res.status === 200) {
        resolve(res.data)
      }
      else {
        console.error(res.data)
        reject(res.data)
      }
    }).catch((error) => {
      console.error(error)
      reject(error)
    })
  })
}

```



