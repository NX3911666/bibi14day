# Promise 的基本使用
```js
//  new 一个Promise，含有两个构造函数（可以理解为参数）reslove要处理的数据，reject抛出错误提示。Es6语法。
        new Promise((resolse,reject)=> {
            setTimeout(() => {
                // resolse('resolse');
                console.log(Promise);
                reject('reject')
            }, 1000);
        }).then(Data => {
            console.log("data");
        }).catch(Error =>{
            console.log("Error");
        })
```
# Promise 的链式调用处理

```js
new Promise ((resolve, reject) => {
            setTimeout(()=> {
                resolve()
            },1000)
        }).then(()=> {
            console.log('第一次网络请求数据');
            console.log('第一次网络请求数据');
            console.log('第一次网络请求数据');
            console.log('第一次网络请求数据');
            console.log('第一次网络请求数据');
            console.log('第一次网络请求数据');
            return new Promise ((resolve , reject ) => {
                setTimeout(() => {
                    resolve()
                }, 1000);
            }).then(()=> {
                console.log('第二次网络请求');
                console.log('第二次网络请求');
                console.log('第二次网络请求');
                console.log('第二次网络请求');
                console.log('第二次网络请求');
                return new Promise ((resolve , reject) => {
                    setTimeout(() => {
                        resolve();
                    }, 1000);
                }).then(()=> {
                    console.log(('第三次网络请求'));
                })
            })
        })
```
# Promise的链式调用简写
```js
//常规写法见上，省略new Promise ，内部 API
new Promise ((resolve, reject)=>{
            setTimeout(() => {
                resolve('简写aaa')
            }, 3000);
        }).then((data)=>{
            console.log(data, '自己处理一次');
            return Promise.resolve(data + '对结果进行第一次处理')
        }).then(data=>{
            console.log(data, '第二次处理');
        })
// Promise内部考虑到链式处理，可直接return 处理
        new Promise ((resolve, reject)=>{
            setTimeout(() => {
                resolve('ccc链式简写')
            }, 5000);
        }).then(data=>{
            console.log(data, '自己处理一次');
            return data + '到这里进行第一次处理';
        }).then(data=>{
            console.log(data, '第二次处理');
        })
```
# Promise.all的使用场景
> 当多个网络请求需要同时满足条件时，处理请求
```js
//Promise.all为数组形式，返回的是一个数组
 Promise.all([
        new Promise((resolve, reject)=>{
            setTimeout(() => {
                resolve({
                    name: '大海',
                    age: '23'
                })
            }, 1000);
        }),
        new Promise ((resolve, reject)=>{
            setTimeout(()=>{
                resolve({
                    name: '小海',
                    age: '14'
                })
            },2000)
        })
        ]).then(results=>{
            console.log(results);
        })
```
![alt 结果](./20210808212654.png)
