title: 几个疑惑
date: 2016-12-02 16:14:30
tags: trouble
description: 几个疑惑
---
通过split串成的数组是真数组吗
通过isArray()检测是的
但是不能使用forEach进行遍历
   ``` js

function tobinary(num){
    return num.toString(2);
}
function getindex1(arr,item){
    var myindex = []
    arr.forEach(function(val,i){
        if (item === val)
            myindex.push(i)
    })
    if (myindex.length > 1)
        return myindex

    else if (myindex.length == 0)
        return -1
    else if (myindex.length == 1)
        return myindex[0]

}
function isArray(o) {
    return Object.prototype.toString.call(o) === '[object Array]';
    console.log(Object.prototype.toString.call(o))
}
var mn = [1,1,1,0,0,0,1,1,1,1,1,0,0,0,0,1,1,0,0,1,1,0,0,0,0,0,0,0,1,0,1,1,1,0,1,1,1,1,0,0,1,0,1,0,1,0,0,1,1,1]
console.log("1: "+getindex1(mn,1)) //返回所有1的索引
console.log("1: "+getindex1(nn,1)) //返回-1
  ```