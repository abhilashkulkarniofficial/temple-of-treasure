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
