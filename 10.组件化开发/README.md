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
# $emit子传父自定义事件

1. 在子组件中通过methods发射事件出去

```javascript
                    methods:{
                        btnClick(item){
                            //发射事件给父组件
                            this.$emit('itemclick', item)
                        }
                    }
```

2. 父组件接收监听事件

```html
    <div id="app">
        <div>
            <!-- 接收事件 -->
            <cpn @itemclick="cpnclick"></cpn>
        </div>
    </div>
```

3. 父组件调用传过来的数据

```js
            methods: {
                cpnclick(item){
                    console.log('cpnclick',item)
                }
            }
```
# 组件访问

1. 父组件访问子组件

```js
//方式一： 不常用 会遍历整个子组件
this.$children.

//方式二： $refs(常用) 绑定要访问的组件
this.$refs.<绑定的标签名>.<属性值>
```
2. 子访问父组件

```js
<cpn ref="aaa"></cpn>

this.$parent.<标签名>.<属性值>
```
3. 插槽slot的基本使用

```js
//1.基本使用<slot></slot>
//2.默认值<slot><button>  </button></slot>
//3.如果内部有多个值，则全部替换
//4.可多个插槽
            <slot>
                <button>提交</button>
            </slot>
```
4. slot具名的使用
```js
                        <td><cpn><span slot="header">我是头部</span></cpn></td>
                        <td><cpn><span slot="main">我是主体</span></cpn></td>
                        <td><cpn><span slot="footer">我是底部</span></cpn></td>

                        <template id="cpn">
                            <div>
                                <slot name="header"></slot>
                                <slot name="main"></slot>
                                <slot name="footer"></slot>
                            </div>
                        </template>
```

