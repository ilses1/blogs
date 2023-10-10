---
title: 手写一个reduce
date: 2023-10-10 17:27:07
categories: 
- 手写  
tags:
---

# 1.reduce是什么？

累计器，
reduce() 方法是一个[迭代方法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array#%E8%BF%AD%E4%BB%A3%E6%96%B9%E6%B3%95)。它按升序对数组中的所有元素运行一个“reducer”回调函数，并将它们累积到一个单一的值中。每次调用时，callbackFn 的返回值都作为 accumulator 参数传递到下一次调用中。accumulator 的最终值（也就是在数组的最后一次迭代中从 callbackFn 返回的值）将作为 reduce() 的返回值。
[Array.prototype.reduce() - JavaScript | MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)

# 2.参数

可以传入一个参数或者两个参数，
有两个参数是，回调函数和初始值，一个参数时，参数为回调函数，初始值为数组的第一个值
reduce(callbackFn)
reduce(callbackFn, initialValue)

callbackFn的参数（accumulator,currentValue,currentIndex,array）=>{}
1.accumulator为上一次调用callbackFn返回的值，第一次时为initialValue，没有initialValue则为数组第一个值
2.currentValue为当前值，
3.currentIndex为当前值索引，
4.array为原数组

# 3.实现一个myreduce

```tsx
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>

</body>
<script>

    Array.prototype.myreduce = function (cb, initcialVal) {

        /* 
        1.如何获取调用方法的数组？
        2.如何实现累积器的返回
        3.如何实现调用自身？
        
        */
        //    原数组
        const oldArr = this
        debugger

        // 第一次的acc 有初始值则初始值，否则为数组第一个 
        let acc = initcialVal ? initcialVal : oldArr[0]

        // 如果有initcialVal则从第一个开始，否则从第二个开始
        let i = initcialVal ? 0 : 1


        for (i; i <= oldArr.length - 1; i++) {
            // 对数组每一项处理
            acc = cb(acc, oldArr[i], i, oldArr)

        }
        return acc
    }


    // 试试
    let arr = [1, 2, 3, 4, 5]

    const arr1 = arr.myreduce((acc, item) => {
        console.log(acc, item)

        return acc += item
    })

    const arr2 = arr.reduce((acc, item) => {

        return acc += item
    })
    console.log('myreduce:', arr1, 'reduce:', arr2);
</script>

</html>
```