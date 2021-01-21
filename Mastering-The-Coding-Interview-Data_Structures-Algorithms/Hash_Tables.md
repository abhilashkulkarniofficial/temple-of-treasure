Implement set() and get() functions of Hash tables:

My implementation:

```
class HashTable {
  constructor(size){
    this.data = new Array(size);
  }

  _hash(key) {
    let hash = 0;
    for (let i =0; i < key.length; i++){
        hash = (hash + key.charCodeAt(i) * i) % this.data.length
    }
    return hash;
  }

  set(key, value){
    let index = this._hash(key)
    if(this.data[index]){
      this.data[index].push([key,value])
      return
    }
    this.data[index] = [[key, value]]
  }

  get(key){
    let index = this._hash(key)
    let arr = this.data[index]
    arr.forEach(val => {
      if(val[0]==key){
        console.log(val[1])
        return
      }
    })
  }
}

const myHashTable = new HashTable(50);
myHashTable.set('grapes', 10000)
// myHashTable.get('grapes')
myHashTable.set('apples', 9)
// myHashTable.get('apples')
myHashTable.set('grapes', 10)
myHashTable.get('grapes')
// myHashTable
```

Improvements:

1. set() function could be cleaner.
2. Perform input checking for get() function

Course Implementation:

```
class HashTable {
  constructor(size){
    this.data = new Array(size);
    // this.data = [];
  }

  _hash(key) {
    let hash = 0;
    for (let i =0; i < key.length; i++){
        hash = (hash + key.charCodeAt(i) * i) % this.data.length
    }
    return hash;
  }

  set(key, value) {
    let address = this._hash(key);
    if (!this.data[address]) {
      this.data[address] = [];
    }
    this.data[address].push([key, value]);
    return this.data;
  }

  get(key){
    const address = this._hash(key);
    const currentBucket = this.data[address]
    if (currentBucket) {
      for(let i = 0; i < currentBucket.length; i++){
        if(currentBucket[i][0] === key) {
          return currentBucket[i][1]
        }
      }
    }
    return undefined;
  }
}

const myHashTable = new HashTable(50);
myHashTable.set('grapes', 10000)
myHashTable.get('grapes')
myHashTable.set('apples', 9)
myHashTable.get('apples')
```

My updated implementation. I've fixed the set() function to update the value if the key already exists.

```
class HashTable {
  constructor(size){
    this.data = new Array(size);
  }

  _hash(key) {
    let hash = 0;
    for (let i =0; i < key.length; i++){
        hash = (hash + key.charCodeAt(i) * i) % this.data.length
    }
    return hash;
  }

  set(key, value){
    let index = this._hash(key)
    if(!this.data[index]){
      this.data[index] = []
      this.data[index].push([key,value])
    }else{
      if(this.get(key)==undefined){
        this.data[index].push([key,value])
      }else{
        this.data[index].forEach(item => {
          if(item[0] == key){
            item[1] = value
            return
          }
        })
      }
    }    
  }

  get(key){
    let index = this._hash(key)
    let arr = this.data[index]
    for(let i = 0; i < arr.length; i++){
      if(arr[i][0] === key){
        return arr[i][1]
      }
    }
  }

  keys(){
    let keys = []
    this.data.forEach(val => {
      val.forEach(item => {
        keys.push(item[0])
      })
    })
    return keys
  }
}

const myHashTable = new HashTable(50);
myHashTable.set('grapes', 10000)
myHashTable.get('grapes')
myHashTable.set('apples', 9)
myHashTable.get('apples')
myHashTable.set('oranges', 10)
myHashTable.set('grapes', 20)
myHashTable.get('grapes')
console.log(myHashTable)
myHashTable.keys()

```

Interview Question:

Recurring First character (Google question)

My initial solution:

```
//Google Question
//Given an array = [2,5,1,2,3,5,1,2,4]:
//It should return 2

//Given an array = [2,1,1,2,3,5,1,2,4]:
//It should return 1

//Given an array = [2,3,4,5]:
//It should return undefined


function firstRecurringCharacter(input) {
  // Input checking
  if(!input || input.length < 1){
    return "Hmmm. Check the input please!"
  }

  let characterObject = {}  // {2:true, 5:true}

  for(let i=0; i<input.length; i++){
    if(characterObject[input[i]]){
      return input[i]
    }else{
      characterObject[input[i]] = true
    }
  }
  return undefined

}

let result = firstRecurringCharacter([2,5,5,2,3,5,1,2,4])
console.log(result)
//Bonus... What if we had this:
// [2,5,5,2,3,5,1,2,4]
// return 5 because the pairs are before 2,2
```

We decreased the time complexity from O(n^2) to O(n) but we increased the space complexity by using hash tables.
