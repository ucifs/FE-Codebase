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

### 获取UA

```js
const UA = typeof window !== 'undefined' && window.navigator.userAgent.toLowerCase();
```

### 判断是否是IE

```js
const isIE = UA && /msie|trident/.test(UA)
```

### 判断是否是IE9

```js
const isIE9 = UA && UA.indexOf('msie 9.0') > 0;
```

### 判断是否是Edge

```js
const isEdge = UA && UA.indexOf('edge/') > 0;
```

### 判断是否是Android

```js
const isAndroid = UA && UA.indexOf('android') > 0;
```

### 判断是否是IOS

```js
const isIOS = UA && /iphone|ipad|ipod|ios/.test(UA);
```

### 判断是否是Chrome

```js
const isChrome = UA && /chrome\/\d+/.test(UA) && !isEdge;
```

### 判断是否为Web环境

```js
const isBrowser = () => {
    return ![typeof window, typeof document].includes('undefined');
};
```

### 检测浏览器是否支持Canvas

```js
const isSupportCanvas = () {
    return document.createElement('canvas').getContext ? true : false;
};
```

### 常用的正则表达式

```js
const isUrl = new RegExp('[a-zA-z]+://[^\s]*') // 网址判断
const isEmail = new RegExp('^\w+([-+.]\w+)@\w+([-.]\w+).\w+([-.]\w+)*$') // 邮箱判断
const isChinese = new RegExp('[\u4e00-\u9fa5]') // 中文判断
const isPhone = new RegExp('^(13[0-9]|14[5|7]|15[0|1|2|3|5|6|7|8|9]|18[0|1|2|3|5|6|7|8|9])\d{8}$') // 中国大陆手机号码
const isIDCard = new RegExp('(^\d{15}$)|(^\d{18}$)|(^\d{17}(\d|X|x)$)') // 身份证
const isPositiveInteger = new RegExp('[0-9]*[1-9][0-9]*') // 正整数
const isNegativeInteger = new RegExp('-[0-9]*[1-9][0-9]*') // 负整数
const isInteger = new regExp('-?\d+') // 整数
```

### URL解析

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

### 数组平均数

```js
const average = (arr) => {
  return arr.reduce((acc, val) => acc + val, 0) / arr.length;
}
```

### 大写每个单词的首字母

```js
const capitalizeEveryWord = (str )=> {
  return str.replace(/\b[a-z]/g, (char) => {
    return char.toUpperCase();
  });
}
```

### 计算数组中某个值的出现次数

```js
const countOccurrences = (arr, value) => {
  return arr.reduce((a, v) => {
    return v === value ? a + 1 : a + 0;
  }, 0)
};
```

### 比较数组之间的区别

```js
const difference = (a, b) => { 
  const s = new Set(b); 
  return a.filter((x) => {
    return !s.has(x);
  }); 
};
```

### 获取数组中的最大值

```js
const arrayMax = (arr) => {
  return Math.max(...arr);
};
```

### 获取数组中的最小值

```js
const arrayMax = (arr) => {
  return Math.min(...arr);
};
```

### 反转字符串

```js
const reverseString = (str) => {
  return [...str].reverse().join('');
};
```

### 数组之和

```js
const sum = (arr) => {
  return arr.reduce((acc, val) => {
      return acc + val;
  }, 0);
}
```

### 数组转字符串

```js
const array2String = function (array) {
  return array.length === 1 ? array[0] : array.join(' ')
}
```