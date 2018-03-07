###10.  Build Tower (6kyu)

	````
	// py
	def tower_builder(n):
    	# build here
	    print n
	    totalStars = 2*n - 1
	    floorList = []
	    for i in range(0, n):
	        strNum = (2*(i + 1)-1)
	        floorList.append( ' '*((totalStars - strNum)/2) + '*'*strNum + ' '*((totalStars - strNum)/2) ) ;
	    return floorList
	````
###11. Counting Duplicates (6kyu)

	````
	// py
	def duplicate_count(text):
	    # Your code goes here
	    lowerStr = text.lower()
	    textArr = list(lowerStr);
	    hashDictionary = {};
	    returnList = [];
	    for element in textArr:
	        if element in hashDictionary.keys():
	            hashDictionary[element] += 1
	        else: 
	            hashDictionary[element] = 1
	    for key, value in hashDictionary.items():
	        if value > 1:
	            returnList.append(key)
	    return len(returnList)
	````
	
	
###12. Dashatize it (6kyu)

	````
	// js
	function dashatize(num) {
	  if (isNaN(num)) {
	    return 'NaN';
	  }
	  if (num === 0 || num === 1) {
	    return num+'';
	  }
	  const numArr = (Math.abs(num)+'').split('');
	  const handledStr = numArr.map((items, index) => {
	    return items % 2 !== 0 ? `-${items}-` : items
	  }).join('');
	  const regedStr = handledStr.replace(/--/g, '-');
	  return regedStr.replace(/^-|-$/g, '');
	}
	
	
	// py
	import math
	import re
	def dashatize(num):
	    if None == num:
	        return 'None'
	    if num == 0 or num == 1:
	        return str(num)
	    numArr = list(str(int(math.fabs(num))))
	    returnArr = []
	    for i in numArr:
	        if int(i) % 2 != 0:
	            returnArr.append('-' + i + '-')
	        else:
	            returnArr.append(i)
	    return re.sub(r'^-|-$',"","".join(returnArr).replace('--', '-'))
	````
###13. Take a picture! (6kyu)

	````
	// py
	def sort_photos(pics):
	    fSort = sorted( pics, key = lambda d: ( int(d.split('.')[0])*1000 + int(d[8:]) ) )
	    sliceList = []
	    if len(fSort) > 5:
	        sliceList = fSort[-5:]
	    else:
	        sliceList = fSort[:]
	    sliceList.append(sliceList[-1][:8] + str(int(sliceList[-1][8:]) + 1))
	    return sliceList
	````
	
	
###14. Sum of Digits / Digital Root (6kyu)

	````
	def digital_root(n):
	    listNum = list(str(n))
	    result = 0
	    for i in listNum:
	        result = result + int(i)
	
	    if len(str(result)) > 1:
	        return digital_root(result)
	    else:
	        return result 
	````
	
###15. Number of trailing zeros of N! (5kyu)

	````
	function zeros (n) {
	  let count = 0
	  while (true) {
	    n = Math.floor(n / 5)    
	    if (n === 0) {
	      break
	    } else {
	      count += n
	    }
	  }
	  return count
	}
	````

###15. Maximum subarray sum (5kyu)

	````
	function maxSequence(array) {
	  if (array.length <= 0) {
	    return 0;
	  }
	  let result = 0;
	  let temp = 0;  
	  array.forEach(item => {
	    temp = temp < 0 ? item : temp + item;
	    result = temp > result ? temp : result
	  });
	  return result
	}
	````
###16.Moving Zeros To The End(5kyu)
	
	````
	var moveZeros = function (arr) {
	  // TODO: Program me
	  const nullZeroArray = [];
	  const zeroArray = [];
	  arr.forEach(ele => {
	    if (ele !== 0) {
	      nullZeroArray.push(ele);
	    } else {
	      zeroArray.push(ele)
	    }
	  });
	  return nullZeroArray.concat(zeroArray);
	}
	````

###17.Calculating with Functions(5kyu)
	
	````
	function common(func, n = num) {
	  return func ? func.call(func, n) : n;
	}
	
	function zero(func) {
	  return common(func, 0);
	}
	function one(func) {
	  return common(func, 1);
	}
	function two(func) {
	  return common(func, 2);
	}
	function three(func) {
	  return common(func, 3);
	}
	function four(func) {
	  return common(func, 4);
	}
	function five(func) {
	  return common(func, 5);
	}
	function six(func) {
	  return common(func, 6);
	}
	function seven(func) {
	  return common(func, 7);
	}
	function eight(func) {
	  return common(func, 8);
	}
	function nine(func) {
	  return common(func, 9);
	}
	
	function plus(n) {
	  return function(x) {
	    return x + n;
	  };
	}
	function minus(n) {
	  return function(x) {
	    return x - n;
	  };
	}
	function times(n) {
	  return function(x) {
	    return x * n;
	  };
	}
	function dividedBy(n) {
	  return function(x) {
	    return x / n;
	  };
	}
	````

###18.Gap in Primes(5kyu)
	
	````
	function gap(g, m, n) {
	  // your code
	  let basicNum = 0;
	  for (let i = m; i < n; i++) {
	    if(isPrime(i)) {
	      if (i - basicNum === g) {
	        return [basicNum, i] 
	      }
	      basicNum = i;
	    }
	  }
	  return null;
	}
	
	
	function isPrime(num) {
	    // 不是数字或者数字小于2
	    if(typeof num !== "number" || !Number.isInteger(num)) {
	        // Number.isInterget 判断是否为整数
	        return false
	    }
	    //2是质数
	    if(num == 2) {
	        return true
	    } else if(num % 2 == 0) {  //排除偶数
	        return false
	    }
	    //依次判断是否能被奇数整除，最大循环为数值的开方
	    var squareRoot = Math.sqrt(num)
	    //因为2已经验证过，所以从3开始；且已经排除偶数，所以每次加2
	    for(var i = 3; i <= squareRoot; i += 2) {
	        if(num % i === 0) {
	            return false
	        }
	    }
	    return true
	}
	
	````

###19.Convert string to camel case(5kyu)
	
	````
	// js 正则
	function toCamelCase(str){
	  return str.replace(/-(\w)|_(\w)/g, (matchStr) => {
	    return matchStr.charAt(1).toUpperCase();
	  })
	}
	// js 非正则 有缺陷
	function toCamelCase(str){
	  if (str.indexOf('_') > 0) {
	    return str.split('_').slice(0, 1) + str.split('_').slice(1).map(items => {
	      return items.camelCase()
	    }).join('');
	  } else {
	    return str.split('-').slice(0, 1) + str.split('-').slice(1).map(items => {
	      return items.camelCase()
	    }).join('');
	  }
	}
	
	// py
	import re
	def to_camel_case(text):
	    #your code here
	    textList = re.split('[-_]',text)
	    resultList = []
	    for index, item in enumerate(textList):
	        if index > 0:
	            resultList.append(item[0].upper() + item[1:])
	        else:
	            resultList.append(item)
	    return ''.join(resultList)
	````
### 20.Fun with trees: array to tree(5kyu)	
	````
	function arrayToTree(array) {
	  return (function binaryTree(i){
	     if(array[i] === undefined)
	      return;
	    return new TreeNode(array[i], binaryTree(i * 2 + 1), binaryTree(i * 2 + 2));
	  })(0);
	};
	var TreeNode = function(value, left, right) {
	  this.value = value;
	  this.left = left;
	  this.right = right;
	};
	````