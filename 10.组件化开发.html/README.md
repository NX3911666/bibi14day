# 组件知识点

1. 如何构造一个组件？

```javascript
const myFirstcomponent = Vue.extend({
            template: "<p>你好，世界</p>"
        })
Vue.component('Firstcomponent',myFirstcomponent) 
···
components: {
                'Firstcomponent': myFirstcomponent
            }
```

2. 全局组件和局部组件

### 即将组件注册在实例中

```javascript
const myFirstcomponent = Vue.extend({
             template: 
             `
             <p>你好 世界</p>
             `
        })
···
//将组件构造器放到实例中  构成局部组件
            components: {
                'Firstcomponent': myFirstcomponent
            },
```



3. 父子组件

### 即将子组件（child）注册到父组件中，在父组件中调用

```javascript
const cpnC2 = Vue.extend({
            template:`
            <div>
                <p>你好我是第二个组件</p>
                <cpn1></cpn1>
            </div>
            `,
            components:{
                cpn1: cpnC1 ,
            }
        })
···
components:{
                cpn2: cpnC2
            },
···

```
# 组件的语法糖

1. 简介模式 使用语法糖构建组件 省略extends

```javascript
Vue.component('cpn1',{
            template:'<p>你好</p>'
        })
        //直接使用
    <div id="app">
        <cpn1></cpn1>
    </div>
```
2. 重构分离写法

### 将组件内容写到 template标签中 进行绑定

```javascript
    <template id="my-cpn3">
        <div>
           <p>我是标题</p>
        </div>
    </template>

    cpn3:{
        template: "#my-cpn3"  //绑定id的标签 #
        }
```
