# Vue学习笔记-class
## 一、直接传入
*原生*
#### html代码
``` html
<p class="class1 class2 ..."></p>
```
***

## 二、传入一个数组
*直接传入数组时，class需要用v-bind做数据绑定*
#### html代码
``` html
<p :class="['box1','box2',...]">独钓寒江雪</p>
```
感觉和原生的差不多，还不知道有什么优劣
> 可以在数组中传入多个对象，这样在data{}中可以动态的改变显示
#### html代码
``` html
<p :class="[{'box1':isShow},{'box2':!isShow},...]">独钓寒江雪</p>
```
#### js代码
``` js
data: {
    isShow: true/false
}
```

***

## 三、用表达式
*可以使用表达式*
#### html代码
``` html
<p :class="['box1','box2',isShow?'box3':'']">独钓寒江雪</p>
```
#### js代码
``` js
data: {
    isShow: true/false
}
```
***

## 四、传入一个对象并在data中动态改变
*这种方式好*
#### html代码
``` html
<p :class="classObj">独钓寒江雪</p>
```
#### js代码
``` js
data:{
    classObj: {
        'box1':true,
        'box2':true,
        'box3':true,
        ...
    }
}
```


