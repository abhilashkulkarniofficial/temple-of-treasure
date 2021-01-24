# Stacks and Queues

### Stacks Implementation

```
class Node {
  constructor(value){
    this.value = value;
    this.next = null;
  }
}

class Stack {
  constructor(){
    this.top = null;
    this.bottom = null;
    this.length = 0;
  }
  peek() {
    if(!this.top){
      return null
    }else{
      return this.top.value
    }
  }
  push(value){
    const newNode = new Node(value)
    if(!this.top){
      this.top = newNode
      this.bottom = newNode
    }else{
      newNode.next = this.top
      this.top = newNode
    }
    this.length++
    
  }
  pop(){
    if(!this.top){
      return null
    }
    if(this.top === this.bottom){
      this.bottom = null
    }
    this.top = this.top.next
    this.length --
    return
  }
  //isEmpty
}

const myStack = new Stack();
myStack.push('Discord')
myStack.push('Udemy')
myStack.push('google')
console.log(myStack.peek())
console.log(myStack)
myStack.pop()
myStack.pop()
myStack.pop()
console.log(myStack)
```

### Stack implementation using arrays

```
class Stack {
  constructor(){
    this.array = [];
  }
  peek() {
    return this.array[this.array.length-1];
  }
  push(value){
    this.array.push(value);
    return this;
  }
  pop(){
    this.array.pop();
    return this;
  }
}

const myStack = new Stack();
myStack.peek();
myStack.push('google');
myStack.push('udemy');
myStack.push('discord');
myStack.peek();
myStack.pop();
myStack.pop();
myStack.pop();
```

### Queue implementation

```
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class Queue {
  constructor(){
    this.first = null;
    this.last = null;
    this.length = 0;
  }
  peek() {
    return this.first
  }
  enqueue(value){
    const newNode = new Node(value)
    if(this.length === 0){
      this.first = newNode
      this.last = newNode
    }else{
      this.last.next = newNode
      this.last = newNode
    }
    this.length++
    return this
  }
  dequeue(){
    if(this.length === 0){
      return this
    }
    if(this.first === this.last){
      this.last = null
    }

    this.first = this.first.next
    this.length--
    return this
  }
  //isEmpty;
}

const myQueue = new Queue();
myQueue.enqueue('Joy')
myQueue.enqueue('Matt')
myQueue.enqueue('Pavel')
myQueue.dequeue()
```
