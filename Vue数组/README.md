# Vue-call()和some()
## 一、v-for
遍历数组。如果遍历的是数字，则从1开始遍历
***
## 二、forEach
*只能遍历真数组，不能遍历伪数组*
> 真数组和伪数组
>- 真数组
>- 伪数组:是一个对象，有length属性和下标
>- 如何判断真伪数组：
>    ``` js
>    arr instanceof Array
>    ```

#### js代码
``` js
forEach((item)=> {
    //...
})
```
***

## 三、call()
*将伪数组转化为真数组*
#### html代码
``` html
<ul ref="lis">
    <li>...</li>
    <li>...</li>
    <li>...</li>
    ...
</ul>
```
> ref 被用来给元素或子组件注册引用信息。引用信息将会注册在父组件的 $refs 对象上。如果在普通的 DOM 元素上使用，引用指向的就是 DOM 元素；如果用在子组件上，引用就指向组件实例：

#### js代码
``` js
// 找到lis下的所有li，并把他放在doms伪数组中
let doms = this.$refs.uls.getElementsByTagName("li");
// 伪数组转为真数组可以使用call(arguments)
let arr = Array.prototype.slice.call(doms);
```
***

## 四、some()
*用于检测数组中的元素是否满足指定条件*
#### js代码
``` javascript
let arr = [1,3,5,7,9];
arr.some((str)=> {
    //如果arr数组中的元素包含有someNumber，则返回true，反之
    return str === someNumber; 
})
```
