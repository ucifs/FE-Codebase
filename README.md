# FE-Codebase

### 类型判断

1、是否是Number
```js
const isNumber = val => {
  return typeof val === 'number';
}
```

2、是否是String
```js
const isString = val => {
  return typeof val === 'string';
}
```

3、是否是对象
```js
const isObject = obj => {
  return obj === Object(obj);
}
```

4、是否是undefined
```js
const isUndefined = val => {
  return val === undefined;
};
```

5、是否是null
```js
const isNull = val => {
  return val === null;
}
```

6、是否是boolean
```js
const isBoolean = val => {
  return typeof val === 'boolean';
}
```

7、是否是函数
```js
const isFunction = val => {
  return typeof val === 'function';
}
```

8、是否是空的
```js
const isEmpty = val => {
  return val == null || !(Object.keys(val) || val).length;
}
```

### 判断浏览器类型
```js

```

### 判断是否为浏览器环境
```js
const isBrowser = () => {
    return ![typeof window, typeof document].includes('undefined');
};
```


### url解析

> 获取查询参数的键值对

```js
const getURLParameters = url =>
  (url.match(/([^?=&]+)(=([^&]*))/g) || []).reduce(
    (a, v) => ((a[v.slice(0, v.indexOf('='))] = v.slice(v.indexOf('=') + 1)), a),
    {}
  );
```

### 平滑滚动到页面顶部
```js
const scrollToTop = () => {
  const c = document.documentElement.scrollTop || document.body.scrollTop;
  if (c > 0) {
    window.requestAnimationFrame(scrollToTop);
    window.scrollTo(0, c - c / 8);
  }
};
```

### 对象复制
#### 浅复制
1、数组方法

```js
arrayObj.slice(0); // 返回一个新数组

arrayObj.concat(); // 返回一个新数组
```

2、for...in

```js
function copy(obj){
    let newObj = {};
    for ( let attr in obj) {
        newObj[attr] = obj[attr];
    }
    return newObj;
}
```

3、对象解构

> 解构的原理是`Object.assgin`

```js
let newObj = {...obj};
```

4、Object.assgin

```js
let newObj = Object.assgin({}, obj);
```

#### 深复制

1、递归

```js
function deepCopy(obj){
    if(typeof obj !== 'object'){
        return obj;
    }
    let newObj = {};
    for ( let item in obj) {
        newObj[item] = deepCopy(obj[item]);
    }
    return newObj;
}
```

2、JSON.stringify(黑魔法)

```js
let newObj = JSON.parse(JSON.stringify(obj));
```
