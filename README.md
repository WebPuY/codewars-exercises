# codewars-exercises

### 做codewars题目的一些想法。
### 目前是kyu4。逻辑题偶尔可以做做kyu4的，算法题最多可以做做kyu5的（还经常做不出来）。
### 主要是javascript，有时会乱入python。新手适合，请高手多提意见多修改。在下感激。

1. Give me a Diamond （6kyu）
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
