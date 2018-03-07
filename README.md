# codewars-exercises

做codewars题目的一些想法。
目前是kyu4。逻辑题偶尔可以做做kyu4的，算法题最多可以做做kyu5的（还经常做不出来）。
主要是javascript，有时会乱入python。新手适合，请高手多提意见多修改。在下感激。

### 4kyu和5kyu在其他md文件中

### 1. Give me a Diamond （6kyu）

````
function diamond(n){
    if( n<=0 || n%2=== 0 ){
        return null;
    } 

    var str = ''; //这是中间一行上面的字符串
    var str2 = ''; //下面的字符串

    var lines = (n-1)/2; //这是上面或者下面的总行数。比如如果n=7，则上下各有三行。

    //每一行都是一定规则的字符串拼接的  
    for(var i = 0;i < lines;i++){
        str += ' '.repeat(lines-i) + '*'.repeat( i*2 + 1 ) + '\n';
        str2 += ' '.repeat(i+1) + '*'.repeat( n-i*2-2 ) + '\n';
    }
    console.log(str + '*'.repeat(n) + '\n' + str2);
    return str + '*'.repeat(n) + '\n' + str2;  
}
````
### 2.Array.diff（6kyu）

````
function array_diff(a, b) {
    if(b.length === 0){
        return a;
    }
    return a.filter(function(item){
        return b.indexOf(item) === -1;
    });

}

// 这个代码啰嗦了。
function array_diff(a, b) {
  if (a.length < 1) {
    return [];
  }
  if (b.length < 1) {
    return a;
  }
  const returnArr = a.filter((items) => {
    return b.join('').indexOf(items) === -1;
  });
  return returnArr;
}
````

### 3.Sort the odd（6kyu）

````
function sortArray(array) {
  // Return a sorted array.
  const sortArr = array;
  let count = -1;
  let temp;
  if (sortArr.length < 1) {
    return [];
  }
  const oddArr = sortArr.filter((items) => {
    return items % 2 !== 0;
  }).sort(function(a, b) {
    return a - b;
  });
  sortArr.forEach((element, index) => {
    if (sortArr[index] % 2 !== 0) {
      count = count + 1;
      oddArr.forEach(item => {
        sortArr[index] = oddArr[count];        
      });
    }
  });
  return sortArr;
}
````

### 4.Count characters in your string（6kyu）

````
function count (string) {  
  // The function code should be here
  let obj = {};
  if (string.length < 1) {
    obj = {};
  }
  string.split('').forEach((element) => {
    if (!obj[element]) {
      obj[element] = 1;
    } else {
      obj[element] ++;
    }
  });
  return obj;
}
````

### 5.CamelCase Method（6kyu）

````
String.prototype.camelCase=function(){
  //your code here
  return this.split(' ').map(item => {
    const itemArr = item.split('');
    const replaceChar = item.slice(0, 1).toUpperCase();
    itemArr.splice(0,1,replaceChar);
    return itemArr.join('');
  }).join('');
}
````

### 6.Format a string of names like 'Bart, Lisa & Maggie'.(6kyu)

````
// javascript
function list(names){
  //your code here
    const nameArr = [];
    names.forEach((item) => {
        nameArr.push(item.name);
    });
    const nameStr = nameArr.join(', ');
    const index = nameArr.join(', ').lastIndexOf(', ');
    const nameStrArr = nameStr.split('');
    index > 0 ? nameStrArr.splice(index, 1, ' &') : nameStrArr;
    return nameStrArr.join('');
}

// python
def namelist(names):
    #your code here
    nameList = list()
    for i in range(0, len(names)):
        nameList.append(names[i].get('name'))
    nameStr = ', '.join(nameList)
    strIndex = nameStr.rfind(', ')
    if strIndex > -1:
        return nameStr[:strIndex] + ' &' + nameStr[strIndex+1:]
    else:
        return nameStr
````

### 7.Which are in?（6kyu）

````
function inArray(array1,array2){
  const resultArr = [];
  array1.forEach(function(element) {
    array2.forEach(function(item) {
      if (item.indexOf(element) >= 0) {
        resultArr.push(element);
      }
    });
  });
  return Array.from(new Set(resultArr)).sort();
}
````

### 8.Tribonacci Sequence（6kyu）

````
// js
function tribonacci(array,num){
    if(array.length>=num){
        array = array.slice(0,num);
    }
    for( ;array.length<num; ){
        array.push(array[array.length-1]+array[array.length-2]+array[array.length-3]);
    }
    return array;
}

// py
def tribonacci(signature, n):
    #your code here
    if n <= len(signature):
        return signature[:n]
    finalist=[]
    finalist=signature
    for i in range(len(finalist),n):
        finalist.append(finalist[i-1]+finalist[i-2]+finalist[i-3])
    return finalist
````

### 9.Reverse words（6kyu）

````
// py
def reverse_words(str):
    strList=str.split(' ')
    otherList=list()
    for i in range(0,len(strList)):
        otherList.append((strList[i])[::-1])
    return ' '.join(otherList)
````
