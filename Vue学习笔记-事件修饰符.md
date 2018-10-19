# Vue学习笔记-事件修饰符
> 第一次写，会不断修改内容
## 一、.stop
*用于阻止事件冒泡*

> 事件冒泡
>- 1
>- 2

#### html代码
``` html
<div>
    <div @click="boxClick()" class="box">
        <button @click.stop="btnClick()">点我</button>
    </div>
</div>
```
#### js代码
``` js
methods: {
    btnClick() {
        console.log("点击了按钮");
    },
    boxClick() {
        console.log("点击了盒子");
    }
}
```
当子元素和父元素都绑定了事件时，触发子元素的事件，会从内到外的触发父元素事件。但有些时候并不希望出现这些情况，Vue提供了事件修饰符<b>.stop</b>
***
## 二、.self
*只会阻止<b style="color:red">自身</b>事件冒泡*
#### html代码
``` html
<div class="bigBox" @click="bigBox()">
    <div @click.self="boxClick()" class="box">
        <button @click="btnClick()">点我</button>
    </div>
</div>
```
#### js代码
``` js
methods: {
    btnClick() {
        console.log("点击了按钮");
    },
    boxClick() {
        console.log("点击了盒子");
    },
    bigBox() {
        console.log("点击了大盒子");
    }
}
```
只会阻止自身的事件冒泡，比如我点了button，那么box的事件不会触发，只会触发bigBox的事件
> 总的来说，<b>.stop</b>和<b>.self</b>都是可以阻止事件冒泡，但是不同的是<b>.self</b>只会阻止自身的事件，但他的父元素及以上依然会触发事件。
***
## 三、.prevent
*阻止默认事件*
#### html代码
``` html
<a href="https://www.baidu.com" @click="aClick()">点击</a>
```
#### js代码
``` js
methods: {
    aClick() {
        console.log("不要跳转");
    }
}
```
阻止a标签的默认跳转
***
## 四、.capture
*添加事件监听器时使用事件捕获模式*
#### html代码
``` html
<div @click.capture="boxClick()" class="box">
    <button @click="btnClick()">点我</button>
</div>
```
#### js代码
``` js
methods: {
    btnClick() {
        console.log("点击了按钮");
    },
    boxClick() {
        console.log("点击了盒子");
    }
}
```
在点击button后，正常来说触发事件冒泡，先输出按钮，在输出盒子；但添加了.capture后，会先触发带有.capture的事件。
> 和冒泡事件相反，.capture是从外向内传递