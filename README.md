# 模块1 作业

## 1. 关于var作用域问题

打印结果为：10 <br>
并且a(x)()的结果均为10 <br>
原因：在for循环中，var的作用域相当于在for这一片区是全局的，所以值是最后一个，执行顺序为：for循环执行完毕=》a(6)() ，当for循环执行完毕，这个时候i = 10，所以不论后面a(x)(),结果都是10 <br>
类比：当把var改为let，那么执行结果为6,执行a(x)()，let是每个独立分开的，所以值不同，结果为x

## 2.

打印结果为：123<br>
原因：var 变量为123，所以打印出结果即123<br>

## 3.找出最小值var arr = [12,34,32,89,4]
 
  ```
  var arr = [12,34,32,89,4];
  let num = (args) => Math.min(...args);
  num(arr);
  ```

## 4.详细说明var,let,const三种声明变量的方式之间的具体差别？
var:没有块的概念，可以跨块访问，不能跨函数访问，支持变量提升<br>
let：只能在块级作用域内访问，不能跨块访问，不能跨函数访问，不支持变量提升，必须先声明后使用<br>
const：必须初始化，只能在块级作用域访问，简单数据类型是不可以修改的，但声明复合类型数据（对象、数组等）的时候，对象的属性是可以被修改的，这是因为对象是引用类型的，const仅保证指针不发生改变，修改对象的属性不会改变对象指针，所以可以被修改。也就是说const定义的引用类型只要指针不发生改变，其他不论如何改变都可以<br>
ES6中大多情况使用const，除非极个别情况明确知道变量的值会改变

## 5.this指代

打印结果：20<br>
原因：当前调用的fn()方法中的this指代obj，所以打印出结果为20<br>

## 6.简述Symbol类型的用途
（1）因为是独一无二的，可以借鉴ios中的单例模式，创建一个全局的单例来共享数据，api<br>
（2）因为symbol类型不能通过Object.keys()或者for...in或者JSON.stringify()来枚举，所以可以把一些不需要对外界操作和访问的属性使用Symbol来定义，让“对内操作”和“对外选择性输出”显得更加优雅

## 7.说说浅拷贝，深拷贝
深拷贝和浅拷贝，对于基础数据类型，效果是一致的<br>
但是对于对象元素包含引用的话，效果是不同的<br>
a = [1,2,3] b = copy(a) b[0] = 9<br>
那么：a = [1,2,3] b = [9,2,3]<br>
假如 b = deepcopy(a) b[0] = 9<br>
那么：a = [1,2,3] b = [9,2,3]<br>
假如：a = [1,2,3,[4,5]] b = copy(a) b[3][0] = 9<br>
那么：a = [1,2,3,[9,5]] b = [1,2,3,[9,5]]<br>
假如：b = deepcopy(a) b[3][0] = 9<br>
那么：a = [1,2,3,[4,5]] b = [1,2,3,[9,5]]<br>
深拷贝和浅拷贝真正的区别在于是否真正获取了一个对象的复制实体，而不是引用<br>
浅拷贝仅仅是指向被复制的内存地址，如果原地址中对象被改变了，那么复制出来的对象也会相应改变<br>
深拷贝开辟了一块新的内存地址用于存放复制对象，与原对象是完全独立的<br>

## 8.谈谈js异步编程，Event loop,宏任务，微任务？
js本身是单线程，执行异步操作的是webapi，也就是浏览器提供的一些api，所以其实对于不同的浏览器，执行js异步操作的结果，也有可能是不同的<br>
同步任务直接在主线程排队依次执行，异步任务不会进主线程，而是进入异步队列，当任务有了结果，把结果放入任务队列，等主线程空了，再从任务队列中依次执行<br>
宏任务是在事件循环下一轮的最开始按照顺序一个一个执行，且浏览器在每个宏任务之间渲染页面<br>
微任务是在主线程空闲时一队一队按照顺序执行，且有些场景下会立即执行：每个回调之后且执行栈中为空，每个宏任务结束之后<br>
初始状态：stack:[], Micro:[], Macro:[]<br>
整体的script代码为一个宏任务，放入Macro,主线程开始执行<br>
当遇到settimeout 异步任务，就将它放入Macro 队列中<br>
当遇到promise.resolve 是一个微任务，放入Micro<br>
当主线程执行完毕，开始询问异步队列，是否有微任务，此时执行promise.resolve<br>
微任务执行完毕，开始新一轮时间循环，执行新的宏任务settimeout <br>
以上过程称之为时间循环

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
TypeScript是Javascript一个超集，包含了Javascript的所有元素，可以载入Javascript代码运行，并扩展了Javascript语法，但是TypeScript需要被编译成JavaScript代码，才能被浏览器支持
Javascript使用变量为弱类型，所以更灵活<br>
TypeScript通过类型注解提供编译时的静态类型检查，引入了类，模块等概念

## 11. 谈谈TypeScript优点
强类型:智能提示，避免编译错误<br>
模块化：引入了module,通过export控制是否可以被外部访问<br>
类型丰富：可以实现类，接口，枚举，泛型，方法重载等<br>










