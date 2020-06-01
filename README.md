# 模块1 作业

## 1. 关于var作用域问题

打印结果为：10
并且a[X]()的结果均为10
原因：var的作用域，执行顺序为：for循环执行完毕=》a[6]() ，当for循环执行完毕，这个时候i = 10，所以不论后面a[x](),结果都是10
类比：当把var改为let，那么执行结果为6,执行a[x]()，结果为x，原因是let的作用域为for循环内部，所以，每次i从0开始，所以打印结果为x


## 2.

打印结果为：123
原因：
类比

## 3.找出最小值var arr = [12,34,32,89,4]
 
  ```
  var arr = [12,34,32,89,4];
  let num = (args) => Math.min(...args);
  num(arr);
  ```

## 4.详细说明var,let,const三种声明变量的方式之间的具体差别？

## 5.this指代

打印结果：20
原因：当前调用的fn()方法中的this指代obj，所以打印出结果为20

## 6.简述Symbol类型的用途


## 7.说说浅拷贝，深拷贝


## 8.谈谈js异步编程，Event loop,宏任务，微任务？


## 9.改进代码

 ```
 new Promise(() => {
      var a = "hello";
      new Promise(() => {
        var b = "lagou";
        new Promise(() => {
          var c = "i love y";
          console.log(a+b+c);
        })
      })
    }).catch(err => console.log(err));
 ```


## 10. 简述TypeScript 与Javascript


## 11. 谈谈TypeScript优点









