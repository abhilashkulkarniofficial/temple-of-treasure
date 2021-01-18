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
