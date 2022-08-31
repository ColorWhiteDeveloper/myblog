#### js闭包

```js
/*
            满足条件:
                1、函数嵌套
                2、内部函数可以访问外层的参数和变量
                3、外部函数返回值必须是内嵌函数
            缺点:
                1、参数和变量不会被垃圾回收机制回收
                2、导致内存泄漏
        */ 
        function myclosure(){
            let count = 0;
            return function(){
                console.log(count++);
            }
        }
        const fn1=myclosure(),fn2=myclosure();
        console.log(fn1);
        fn1();// 0,此时fn1中的count没有被销毁 
        fn1();// 1
        fn2();// 0,开辟新的内存，fn2中的count为0
        fn1();// 2
```

