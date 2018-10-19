# Vue搜索案例
## 案例介绍
通过更改text中的文字，动态的渲染li中的内容
***
## 案例分析
### 一、搭建静态页面
初始数据students
``` js
data: {
    ...
    students: [
        {name: '张三', sex: '女', age: 19, phone: '18921212121'},
        {name: '李四', sex: '男', age: 29, phone: '18921221121'},
        ......
    ],
    ...
}
```
在li标签中使用v-for将students中的数据遍历出来并渲染
> v-for：基于源数据多次渲染元素或模板块。此指令之值，必须使用特定语法 <b>item in items</b>。item为当前遍历元素的别名
``` html
...
<ul v-for="stu in students" :key="index">
    <li>{{stu.name}}</li>
    <li>{{stu.sex}}</li>
    <li>{{stu.age}}</li>
    <li>{{stu.phone}}</li>
</ul>
...
```

### 二、处理逻辑
*通过text内容来改变li中的内容*

v-model双向绑定text组件
``` html
<text v-model="keyword"></text>
```
如果要实现搜索功能，首先要创建一个“过滤器”,将keyword传入过滤器，
从哪里找呢，从students中找；
怎么找？使用students.filter来过滤
通过向Array.filter()中传入
> filter() 方法创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素。
``` js
searchList(keyword) {
    return this.students.filter((student)=> {
        if (student.name.includes(keyword)) {
            return student;
        }
    })
}
```
