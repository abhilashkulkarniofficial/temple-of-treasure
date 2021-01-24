# Linked List

### Singly LinkedList Implementation

```
class Node {
  constructor(value){
    this.value = value
    this.next = null
  }
}

class LinkedList {
  constructor(value) {
    this.head = {
      value: value,
      next: null
    };
    this.tail = this.head;
    this.length = 1;
  }
  append(value) {
    // My Implementation
    // let newNode = {
    //   value: value,
    //   next: null
    // }

    // let currentNode = this.head

    // while(currentNode.next != null){
    //   currentNode = currentNode.next
    // }

    // currentNode.next = newNode

    // this.tail = newNode
    // this.length++

    // Course Implementation
    // const newNode = {
    //   value: value,
    //   next: null
    // }

    const newNode = new Node(value)
    this.tail.next = newNode
    this.tail = newNode
    this.length++

  }

  prepend(value){
    // const newNode = {
    //   value: value,
    //   next: this.head
    // }

    const newNode = new Node(value)
    newNode.next = this.head
    this.head = newNode
    this.length ++
  }

  insert(index, value){
    if(index === 0){
      this.prepend(value)
      return
    }else if(index >= this.length){
      this.append(value)
      return
    }

    let newNode = new Node(value)
    let leader = this.traverseToIndex(index -1)

    // let currentNode = this.head

    // while(currentNode.next != null && index != 1){
    //   currentNode = currentNode.next
    //   index--
    // }

    let nextNode = leader.next
    leader.next = newNode
    newNode.next = nextNode
    this.length++
  }

  traverseToIndex(index){
    let currentNode = this.head
    while(index!=0){
      currentNode = currentNode.next
      index--
    }
    return currentNode
  }

  remove(index){
    if(index <= 0){
      this.head = this.head.next
      return
    }else if(index >= this.length){
      console.log(`Index ${index} is empty. Please check the index`)
      return
    }

    let leader = this.traverseToIndex(index - 1)
    let nextNode = leader.next
    leader.next = nextNode.next
    this.length --

  }

  reverse(){
    if(this.length == 1){
      return this.head
    }
    
    let prevNode = null
    let leaderNode = this.head

    while(leaderNode != null){
      let tempNode = leaderNode.next
      leaderNode.next = prevNode
      prevNode = leaderNode
      leaderNode = tempNode
    }

    let tempNode = this.head
    this.head = this.tail
    this.tail = tempNode
  }

  printList(){
    const array = []
    let currentNode = this.head
    while(currentNode != null){
      array.push(currentNode.value)
      currentNode = currentNode.next
    }
    return array
  }
}

let myLinkedList = new LinkedList(10);
myLinkedList.append(5);
myLinkedList.append(16);
myLinkedList.prepend(30);
myLinkedList.insert(2, 99);
myLinkedList.insert(30, 88);
console.log(myLinkedList.printList())
// myLinkedList.remove(30);
myLinkedList.reverse()
console.log(myLinkedList.printList())
```

### Doubly LinkedList Implementation

```
class Node {
  constructor(value){
    this.value = value
    this.next = null
    this.prev = null
  }
}

class DoublyLinkedList {
  constructor(value) {
    this.head = {
      value: value,
      next: null,
      prev: null
    };
    this.tail = this.head;
    this.length = 1;
  }

  append(value) {
    const newNode = new Node(value)
    this.tail.next = newNode
    newNode.prev = this.tail
    this.tail = newNode
    this.length++
  }

  prepend(value){
    const newNode = new Node(value)
    this.head.prev = newNode
    newNode.next = this.head
    this.head = newNode
    this.length++
  }

  insert(index, value){
    if(index === 0){
      this.prepend(value)
      return
    }else if(index >= this.length){
      this.append(value)
      return
    }

    let newNode = new Node(value)
    let leader = this.traverseToIndex(index -1)
    let nextNode = leader.next
    leader.next = newNode
    newNode.prev = leader
    newNode.next = nextNode
    nextNode.prev = newNode
    this.length++
  }

  remove(index){
    if(index <= 0){
      this.head = this.head.next
      return
    }else if(index >= this.length){
      console.log(`Index ${index} is empty. Please check the index`)
      return
    }

    let leader = this.traverseToIndex(index - 1)
    let currentNode = leader.next
    let nextNode = currentNode.next
    leader.next = nextNode
    nextNode.prev = leader
    this.length --

  }

  traverseToIndex(index){
    let currentNode = this.head
    while(index!=0){
      currentNode = currentNode.next
      index--
    }
    return currentNode
  }

  printList(){
    const array = []
    let currentNode = this.head
    while(currentNode != null){
      array.push(currentNode.value)
      currentNode = currentNode.next
    }
    return array
  }
}

let myLinkedList = new DoublyLinkedList(10);
myLinkedList.append(5);
myLinkedList.append(16);
myLinkedList.prepend(30);
myLinkedList.insert(2, 99);
myLinkedList.insert(30, 88);
console.log(myLinkedList.printList())
myLinkedList.remove(2);
console.log(myLinkedList.printList())
```
