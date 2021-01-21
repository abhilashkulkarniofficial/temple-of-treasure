# Arrays

### Create a function that reverses a string:

My first solution
```
function reverse(str){
  let strArray = str.split('')
  let back = strArray.length - 1
  let front = 0
  while(front < back){
    let temp = strArray[front]
    strArray[front] = strArray[back]
    strArray[back] = temp
    front++
    back--
  }
  return strArray.join('')
}

let reversedString = reverse('Hi! My name is Abhilash')
console.log(reversedString)
```
Improvements:
1. Perform input checking before performing operations on input

Course Solutions:

Solution 1:
```
function reverse(str){
  // Performing inputing cheching here
  if(!str || typeof str != 'string' || str.length < 2 ) return str;
  
  const backwards = [];
  const totalItems = str.length - 1;
  for(let i = totalItems; i >= 0; i--){
    backwards.push(str[i]);
  }
  return backwards.join('');
}
```

Solution 2:
```
function reverse2(str){
  //check for valid input
  return str.split('').reverse().join('');
}
```

Solution 3:
```
const reverse3 = str => [...str].reverse().join('');
```

### Given 2 arrays that are sorted, merge the arrays in sorted order.

My first solution:
```
function mergeSortedArrays(array1, array2){
  // Check the input
  if(array1 == undefined) return "Not what I was expecting. Please check input"
  else if(array1.length == 0) return array2
  else if(array2 == undefined || array2.length == 0) return array1

  let counter1 = 0
  let counter2 = 0
  let final_array = []

  while(counter1 < array1.length && counter2 < array2.length){
    if(array1[counter1] <= array2[counter2]){
      final_array.push(array1[counter1])
      counter1++
    }else{
      final_array.push(array2[counter2])
      counter2++
    }
  }

  if(counter1 == array1.length){
    for(let i=counter2; i<array2.length; i++){
      final_array.push(array2[i])
    }
  }else{
    for(let i=counter1; i<array1.length; i++){
      final_array.push(array1[i])
    }
  }

  return final_array
}

// mergeSortedArrays()
mergeSortedArrays([0,3], [3,4,6,30]);
```

Course Solutions:

Solution 1:
```
function mergeSortedArrays(array1, array2){
  if(array1.length === 0) {
    return array2;
  }
  if(array2.length === 0) {
    return array1;
  }

  const mergedArray = [];
  let array1Item = array1[0];
  let array2Item = array2[0];
  let i = 1;
  let j = 1;

  while (array1Item || array2Item){
   if(array2Item === undefined || array1Item < array2Item){
     mergedArray.push(array1Item);
     array1Item = array1[i];
     i++;
   }   
   else {
     mergedArray.push(array2Item);
     array2Item = array2[j];
     j++;
   }
  }
  return mergedArray;
}

mergeSortedArrays([0,3,4,31], [3,4,6,30]);
```

This solution uses only 1 while loop by adding 2 variables, array1Item and array2Item and checking if they are not undefined while pushing.
