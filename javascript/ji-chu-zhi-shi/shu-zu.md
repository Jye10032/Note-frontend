### 模拟队列/堆
利用 js 中数组自带的 push、pop、shift 函数
```javascript
let arr = [1, 2, 3];
arr.push(4);
console.log(arr); // 输出: [1, 2, 3, 4]

let lastElement = arr.pop();

console.log(lastElement); // 输出: 4
console.log(arr); // 输出: [1, 2, 3]


let front = arr.shift(); // 移除队头的元素

console.log(front); // 输出: '1'
console.log(arr); // 输出: ['2', '3']

```
### 排序
数组的 sort 函数
```javascript
intervals.sort((a, b) => {
  //if(a[0] - b[0] <= 0)return [a,b];
  //else if(a[0] - b[0] > 0)return [b,a];
});

//1.二维数组的排序
let intervals = [[1,3],[2,6],[8,10],[15,18]];

intervals.sort((a, b) => a[0] - b[0]);

console.log(intervals); // 输出: [[1, 3], [2, 6], [8, 10], [15, 18]]

//2.按照字符串的长度排序：
let strings = ['short', 'medium', 'very long string'];
strings.sort((a, b) => a.length - b.length);

//3.按照字符串的字母顺序排序（不区分大小写）：
let strings = ['Apple', 'banana', 'Cherry'];
strings.sort((a, b) => a.toLowerCase().localeCompare(b.toLowerCase()));

//4.对对象数组按照某个属性值排序：
let objects = [{name: 'John', age: 23}, {name: 'Jane', age: 21}, {name: 'Oliver', age: 25}];
objects.sort((a, b) => a.age - b.age);

//5.两个比较条件的排序
let intervals = [[1,3],[2,6],[1,2],[2,3]];

intervals.sort((a, b) => {
    if (a[0] - b[0] === 0) {
        return a[1] - b[1]; // 如果第一个元素相等，那么根据第二个元素排序
    } else {
        return a[0] - b[0]; // 首先根据第一个元素排序
    }
});

console.log(intervals); // 输出: [[1, 2], [1, 3], [2, 3], [2, 6]]
```

### push([l, r]); 和 push({l, r}); []和{}的区别
p.push([l, r]); 和 p.push({l, r}); 都是向数组 p 添加一个新元素，但是添加的元素的类型和结构是不同的。
**p.push([l, r]); 添加的是一个数组**，这个数组包含两个元素 l 和 r。
例如，如果 l 是 1，r 是 2，那么添加的元素是 [1, 2]。
**p.push({l, r}); 添加的是一个对象**，这个对象有两个属性 l 和 r，属性值分别是 l 和 r 的值。例如，如果 l 是 1，r 是 2，那么添加的元素是 {l: 1, r: 2}。
```javascript
let l = 1, r = 2;
let p = [];

p.push([l, r]);
console.log(p); // 输出: [[1, 2]]

p = []; // 清空数组

p.push({l, r});
console.log(p); // 输出: [{l: 1, r: 2}]
```
## 数值问题
### 数据类型
typeof xx：查询xx的数据类型
NaN：Not a Number
infinity：无穷，有正负之分
undefined：为空，不存在
null：存在但没有定义
![image.png](https://cdn.nlark.com/yuque/0/2023/png/39218847/1699515252936-e20a0965-0da4-44ff-b9ac-af4f854db122.png#averageHue=%23d1cfc7&clientId=u9b696ebf-c52b-4&from=paste&height=336&id=uc27b9230&originHeight=605&originWidth=905&originalType=binary&ratio=1.7999999523162842&rotation=0&showTitle=false&size=306905&status=done&style=none&taskId=ub8aa9aaf-070b-40de-972f-df7bb291483&title=&width=502.7777910968407)
### 数值转换
#### parse
parseInt（string,radix）：将字符串转换为int

- string: 必需，要被解析的字符串
- radix： 可选，表示要被解析的数字的基数，该值介于 2~36 之间，如果省略该参数或其值为 0 ， 则数字将以 10 为基数来解析。如果以 0x 或 0X 开头，将以 16 为基数，如果小于 2 或大于 36(不包括0）， 则返回 NAN 

parseInt 是 JavaScript 中的一个全局函数，用于将字符串转换为整数。以下是其基本用法：
parseInt(string, radix);
参数说明：

- string：必需，要被解析的字符串。
- radix：可选，表示要解析的数字的基数。该值介于 2 ~ 36 之间。如果省略该参数或其值为 0，则数字将以 10 为基数来解析。如果它以 "0x" 或 "0X" 开头，将以 16 为基数。如果该参数小于 2 或大于 36，则 parseInt() 将返回 NaN。

示例：
parseInt("10");       // 返回 10
parseInt("19", 10);   // 返回 19 (10进制)
parseInt("11", 2);    // 返回 3  (2进制)
parseInt("17", 8);    // 返回 15 (8进制)
parseInt("1f", 16);   // 返回 31 (16进制)
parseInt("100", 36);  // 返回 1296 (36进制)
注意：parseInt 会从字符串的开头开始解析数字，直到遇到一个无法被解析为数字的字符，然后返回已经解析的整数部分。如果字符串的第一个字符无法被解析为数字，parseInt 将返回 NaN。
parseInt（）：将字符串转换为int
' parseInt（'8a'）'//8
parseFloat（）：将字符串转化为float类型
#### Base64
javascript使用unicode字符集
ASCII码和Base64的相互转化
btoa（）：转化为base64编码
atob（）：base64转换为原来的值
//汉字不能转换
### 数值判断
isNaN （）：判断一个值是否为NaN
isFinite（）：判断一个值是否为正常的数

### 查询位置
#### index.Of()
```
const arr = [1, 2, 3, 4, 5];

console.log(arr.indexOf(3)); // 输出: 2
console.log(arr.indexOf(6)); // 输出: -1

const str = 'Hello, World!';

console.log(str.indexOf('World')); // 输出: 6
console.log(str.indexOf('JavaScript')); // 输出: -1


index.Of() 应用

1.判断一个变量是否为数组

// 使用constructor判断
function isArray(arr) {
    return arr.constructor.toString().indexOf("Array") > -1;
    //arr.constructor.toString() 的值为function Array() { [native code] }，表示 Array 构造函数是 JavaScript 的内置构造函数，其实现由底层的 JavaScript 引擎提供。
}


```