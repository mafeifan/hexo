---
title: for&forEach
date: 2017-10-31 11:54:13
tags: javascript
---

来源看这里：https://github.com/reactjs/redux/commit/5b586080b43ca233f78d56cbadf706c933fefd19

之前的代码是

`listeners.slice().forEach(listener => listener())`

被修改成了

```
var currentListeners = listeners.slice()
for (var i = 0; i < currentListeners.length; i++) {
  currentListeners[i]()
}
```

<!--more-->

因为forEach性能比for循环低。这里还给出实际例子 http://jsfiddle.net/ssSt5/2/

```
var arr = [];
for (var i = 0; i < 100000; i++) arr[i] = i;

var numberOfRuns = 100;

function runTest(name, f) {
    var totalTime = 0;
    console.time(name);

    for (var r = 0; r < numberOfRuns; r++) {
        f();
    }

    return console.timeEnd(name);
}

function testFunction(v) {
    v;
}

var forTime = runTest('for', function() {
    for (var j = 0; j < arr.length; j++) {
        testFunction(arr[j]);
    }
});

var forEachTime = runTest('forEach', function() {
    arr.forEach(testFunction);
});

```

运行结果：
```
for: 13.484130859375ms
forEach: 192.06494140625ms
```

### forEach相比普通的for循环的优势在于对稀疏数组的处理，会跳过数组中的空位。

在浏览器里运行下
```
var arr = new Array(1000);

arr[0] = 1;
arr[99] = 3;
arr[999] = 5;
// for循环
for (var i = 0, l = arr.length; i < l; i++) {
    console.log('arr[%s]', i, arr[i]);
}
console.log('i :' , i);


// for - in 循环
var count = 0;
for(var j in arr){
    count ++ ;
    if(arr.hasOwnProperty(j)){
        console.log('arr[%s]', j, arr[j]);
    }
}
console.log('count : ', count);
```




参考：
http://mp.weixin.qq.com/s/BmSeCZFZrpkCGk_mmCYNAQ
https://segmentfault.com/q/1010000007977209