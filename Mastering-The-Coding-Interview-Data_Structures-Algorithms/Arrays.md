Create a function that reverses a string:
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

