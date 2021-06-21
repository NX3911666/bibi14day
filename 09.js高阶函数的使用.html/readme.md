# 高阶函数
>

## 编程范式

1. 命令式编程 声明试编程

2. 面向对象编程(第一公民 对象) 函数式编程(第一个公民 函数)

### 几种高阶函数

1. filter()函数  返回类型 true and false  true过滤符合条件的数值，不满足过滤掉

语法：array.filter(function(currentValue,index,arr), thisValue)

```
    const nums = [56, 12 ,56 ,78 ,75, 80, 65]
        let Newnums = nums.filter(function(n ,index, self ){
            return n % 2 !==0; 
            
        })
        console.log(Newnums)  
```

2. map()函数的使用 ：对前面的数组进行映射

```
    let New2nums = Newnums.map(function(n){
            return n * 2
        })
        console.log(New2nums)
```

3. reduce()函数的使用: 对前面的值进行汇总 
```
   let New3nums = New2nums.reduce(function(preValue, n){
            return preValue + n
        },0)
        console.log(New3nums)
```

