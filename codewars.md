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
	
### 21. Simple Pig Latin(5kyu)
	````
	// 6kyu is better
	function pigIt(str){
	  //Code here
	  return str.split(' ').map((items) => {
	    return items.slice(1) + items.slice(0, 1) + 'ay';
	  }).join(' ');
	}
	````

### 22. Convert PascalCase string into snake_case(5kyu)
	````
	function toUnderscore(string) {
	  if (/^[0-9]/g.test(string)) {
	    return string + '';
	  }
	  return string.replace(/[A-Z]/g, function(element) {
	    return `_${element}`.toLowerCase()
	  }).split('').slice(1).join('')
	}
	````
	
### 23. Function Cache(5kyu)
	````
	function cache(func) {
	  // do your magic here
	  var cacheObj = {};
	  return function () {
	    var args = JSON.stringify(arguments);
	    if (!cacheObj.hasOwnProperty(args)) {
	      cacheObj[args] = func.apply(null, arguments);
	    }
	    return cacheObj[args];
	  };
	}
	````

### 24. First non-repeating character(5kyu)
	````
	// so wordy
	function firstNonRepeatingLetter(s) {
	  // Add your code here
	  const hashObj = {};
	  const copyS = s;
	  copyS.toLowerCase().split("").forEach(items => {
	    if (hashObj[items]) {
	      hashObj[items] ++;
	    } else {
	      hashObj[items] = 1;
	    }
	  });
	  const strArr = Object.keys(hashObj).filter((items) => {
	    return hashObj[items] === 1;
	  });
	  const repeatArr = s.split('').filter(item => {
	    return strArr.some(items => {
	      return item.toLowerCase() === items;
	    });
	  });
	  return repeatArr[0] || '';
	}
	````

### 25. Integers: Recreation One(5kyu)
	````
	function getMutis(item) {
	  const primeArr = [];
	  for(let i = 1; i <= item; i++) {
	    if(item % i === 0) {
	      primeArr.push(i);
	    }
	  }
	  // console.log(primeArr);
	  const sum = primeArr.reduce((sum, item) => {
	    return sum + item*item;
	  });
	  // console.log(sum);
	  return sum;
	}
	
	function listSquared(m, n) {
	  // mn之间数的集合
	  const numsMn = [];
	  // 质数集合
	  const primeArr = [];
	  for (let i = m; i < n; i++) {
	    numsMn.push(i);
	  }
	  return numsMn.filter((item) => {
	    // 求item的乘数因子
	    return Math.sqrt(getMutis(item)) % 1 === 0;
	  }).map((items) => {
	    return [
	      items, getMutis(items)
	    ]
	  });
	}
	````

### 26.Pete, the baker (5kyu)
	````
	// so wordy
	function cakes(recipe, available) {
	  // TODO: insert code
	  let resultNum = 0;
	  const desclipe = [];
	  const valueArr = [];
	  const timeArr = [];
	  const recipeArr = Object.keys(recipe);
	  const availableArr = Object.keys(available);
	  if (recipeArr.length > availableArr.length) {
	    return 0;
	  }
	  recipeArr.forEach(recipes => {
	    availableArr.forEach(availables => {
	      if (availables === recipes) {
	        desclipe.push(recipes);
	        if (recipe[recipes] > available[availables]) {
	          valueArr.push(recipes);
	        }
	
	        timeArr.push(Math.floor(available[availables] / recipe[recipes]));
	      }
	    });
	  });
	  if (desclipe.length !== recipeArr.length) {
	    return 0;
	  }
	  if (valueArr.length > 0) {
	    return 0;
	  }
	  resultNum = timeArr.sort((a,b) => {return a-b;})[0];
	  return resultNum;
	}
	````
### 27.Strip Comments (4kyu)
	````
	function solution(input, markers){
	  const returnArr = []
	  input.split('\n').forEach(items => {
	    const isHave = markers.every(marker => {
	      return items.indexOf(marker) < 0
	    })
	    if(isHave) {
	      returnArr.push(items)
	    } else {
	      markers.map(marker => {
	        items.indexOf(marker) > -1 ? returnArr.push(items.slice(0, items.indexOf(marker)).trim()) : ''
	      })
	    }
	  })
	  return returnArr.join('\n')
	}
	````
	
### 27.Twice linear (4kyu)
	````
	function dblLinear(n) {
	  if(n < 0) return [];
	  const returnArr = [];
	  returnArr[0] = 1
	  for (let i = 0; i < n * 5; i++) {
	    let x = 2 * returnArr[i] + 1;
	    returnArr.push(x)
	    let y = 3 * returnArr[i] + 1;
	    returnArr.push(y)
	    // console.log(x, y)
	  }
	  return Array.from(new Set(returnArr)).sort((a,b) => {return a-b;})[n];
	}
	````

### 27.Snail (4kyu)
	````
	function snail(matrix) {
	    if (matrix == null || matrix.length == 0) {
	        return;
	    }
	    var rows = matrix.length;
	    var cols = matrix[0].length;
	    var start = 0;
	    var result = [];
	
	    while (cols > start * 2 && rows > start * 2) {
	        var endX = cols - 1 - start;
	        var endY = rows - 1 - start;
	        //从左到右打印一行
	        for (var i = start; i <= endX; i++) {
	            result.push(matrix[start][i]);
	        }
	        //从上到下打印一行
	        if (start < endY) {
	            for (var i = start + 1; i <= endY; i++) {
	                result.push(matrix[i][endX]);
	            }
	        }
	        //从右到左打印一行
	        if (start < endX && start < endY) {
	            for (var i = endX - 1; i >= start; i--) {
	                result.push(matrix[endY][i]);
	            }
	        }
	        //从下到上打印一行
	        if (start < endX && start < endY - 1) {
	            for (var i = endY - 1; i >= start + 1; i--) {
	                result.push(matrix[i][start]);
	            }
	        }
	        start++;
	    }
	    return result
	}
	````
### 27.Objectify a URL Query String (4kyu)
	````
	function convertQueryToMap(query) {
	  // add your code here
	  const queryObjArr = query.split('&');
	  const returnObj = {};
	  queryObjArr.forEach(items => {
	    let item = items.split('=');
	    let keys = item[0].split('.');
	    let temp = returnObj;
	    for (let i = 0; i < keys.length; i++) {
	      if (i == keys.length - 1) {
	        temp[keys[i]] = typeof item[1] == "string" ? decodeURIComponent(item[1]) : item[1];
	      } else {
	        if (!(keys[i] in temp))
	          temp[keys[i]] = {};
	        temp = temp[keys[i]];
	      }
	    }
	  });
	  return returnObj;
	}
	````


	### 28.Next bigger number with the same digits (4kyu)

	````
	function nextBigger(n){
		// 先判断有没有最大值 如果是从大到小排列的数字，肯定是最大值
		// 如果不是最大值，则从右边开始找，【个位 十位】是否是从大到小排列。如果判断完毕，判断【个位 十位 百位】。依次增加

		const str = String(n);
		const numArr = str.split('');
		const slicedArr = numArr.slice(0);
		if (isSorted(numArr)) {
			return -1;
		}
		return getCorrectNum(slicedArr);

		function getCorrectNum(arr) {
			let tempArr = [];
			let correctArr = [];
			let correctNum = -1;
			let copyTempArr = [];
			let tempCorrectArr = [];
			for (let i = 2; i <= arr.length; i += 1) {
				tempArr = arr.slice(-i);
				copyTempArr = tempArr.slice(0);
				if (!isSorted(tempArr)) {
					// 方法1: 如果在第i位开始不是有序数组了。比如[2, 1, 8, 3, 1, 1], 倒序1开始不是有序数组，截取[1, 8, 3, 1, 1]。从右边依次把[1],[1, 1],[3, 1, 1]换到数组头, 31118。再把1118从小到大排列
					// 方法2: 如果在第i位开始不是有序数组了。比如[1, 8, 3, 1, 1], 先后面的排序11138 => 31118
					const tempNum = copyTempArr.join('') * 1; // 18311
					const length = copyTempArr.length - 1
					for(let j = length; j >= 0; j -= 1) {
						tempCorrectArr = copyTempArr.slice(j).concat(copyTempArr.slice(0, j))
						correctArr = tempCorrectArr.splice(0,1).concat(tempCorrectArr.sort((a,b)=> a-b))
						correctNum = correctArr.join('') * 1  // 31118
						if (correctNum > tempNum) {
							return arr.slice(0, -i).concat(correctArr).join('') * 1;
						}
					}
				}
			}
			return -2;
		}
		// 判断是否是从大到小的有序数组
		function isSorted(arr) {
			const arrPre = arr.slice(0);
			const sortedStr = arr.sort((a,b) => b - a).join('');
			return arrPre.join('') === sortedStr;
		}
	}

	````