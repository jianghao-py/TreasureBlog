```javascript
// 方式一
// request.js
import axios from 'axios';

export function request(config){
   axios.defaults.baseURL = "url地址";

   axios(config.url).then(res=>{
       config.success(res);
   }).catch(err=>{
       cofig.fail(err);
   })
}


// 使用request.js
import {request} from "xxx";
request({
    url:'xxx',
    success:res=>{
        console.log(res);
    },
    fail:err=>{
        console.log(err);
    }
});



// 方式二
// request.js
import axios from 'axios';

return new Promise((resolve,reject)=>{
    let instance = axios.create({
        baseURL:"xxx",
        timeout:5000
    });

    instance(config).then(res=>{
        resolve(res);
    }).catch(err=>{
        reject(err);
    })
})


// 使用request.js
import {request} from "xxx";
request({
    url:"xxx"
}).then(res=>{
    console.log(res);
}).catch(err=>{
    console.log(err);
});




// 最终方式
// request.js
import axios from 'axios';

let instance = axios.create({
    baseURL:"xxx",
    timeout:5000
});
// 因为axios本身就是基于Promise实现的
return instance(config);


// 使用request.js
import {request} from "xxx";
request({
    url:"xxx"
}).then(res=>{
    console.log(res);
}).catch(err=>{
    console.log(err);
});
```