# Check Array Formation Through Concatenation

You are given an array of distinct integers arr and an array of integer arrays pieces, where the integers in pieces are distinct. Your goal is to form arr by concatenating the arrays in pieces in any order. However, you are not allowed to reorder the integers in each array pieces[i].

Return true if it is possible to form the array arr from pieces. Otherwise, return false.

### My Initial solution
```
// const arr = [91, 4, 64, 78]
// const pieces = [[78],[4,64],[91]]
// true

// const arr = [15,88]
// const pieces = [[88],[15]]
//true

// const arr = [49,18,16]
// const pieces = [[16,18,49]]
// false

// const arr = [85]
// const pieces = [[85]]
// true

const arr = [1,3,5,7]
const pieces = [[2,4,6,8]]  
// false

var canFormArray = function(arr, pieces) {
  let i =0
  while(i<arr.length){
    let arrnum = arr[i]
    let isSubset = false

    for(let j=0; j<pieces.length; j++){
      if(pieces[j].includes(arrnum)){
        // console.log(arr[i], pieces[j])
        
        
        pieces[j].forEach(val => {
          if(val == arr[i]){
            isSubset = true
            i++
          }else{
            isSubset = false
          }
        })

      }
    }

    if(!isSubset) return false
  }

  return true
};

canFormArray(arr, pieces)
```

