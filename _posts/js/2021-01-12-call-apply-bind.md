---
layout: post
toc: true
title: "call apply bind"
categories: javascript
tags: ["js基础"]
author:
  - huangxx
---

太基础的知识点，比如这三个方法的作用，传参等本文不涉及，主要是记录比较容易忽略的点。

### call

#### 知识点
1. 第一个参数传null，undefined等，内部会将函数中的this指向window。

#### 手写一个call

```javascript
  // 手写call
  Function.prototype.myCall = function(obj, ...args) {
    let content = obj || window;
    let fn = Symbol();
    // 将函数版绑定在对象上
    content[fn] = this;
    let res = content[fn](...args);
    delete content[fn];
    return res;
  }
  let obj = {
    name: 'Tom',
    sayName: function(age, like) {
      console.log(`${this.name}:${age},${like}`);
    }
  }
  
  let fn = obj.sayName;
  fn.myCall(obj, 12, 'girl');
```

### apply

### bind
