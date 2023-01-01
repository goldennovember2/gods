# Stack

**LIFO, Last-in first-out**

![Queue](../images/data-structures/stack.png)

### Definition
A stack (sometimes called a “push-down stack”) is an ordered collection of items where the addition of
new items and the removal of existing items always takes place at the same end. 
This end is commonly referred to as the “top.” 
The end opposite the top is known as the “base.”

### Use Cases
Every web browser has a Back button. 
As you navigate from web page to web page,
those pages are placed on a stack (actually it is the URLs that are going on the stack)


### Operations
* `Size()` returns the number of items on the stack.
* `Push(item)` adds a new item to the top of the stack.
* `Pop()` removes and returns the top item from the stack.
* `Peek()` returns the top item from the stack.
* `IsEmpty()` tests to see whether the stack is empty and returns a boolean value.

### Implementation

```go
type Stack struct {
    items []int
}

// Size() returns the number of items on the stack.
func (s *Stack) Size() int {
    return len(s.items)
}

// Push(item) adds a new item to the top of the stack.
func (s *Stack) Push(i int) {
    s.items = append(s.items, i)
}

// Pop() will remove a value at the end and return the item.
func (s *Stack) Pop() int {
    l := s.Size()
    toRemove := s.items[l-1]
    s.items = s.items[:l-1]
    return toRemove
}

// Peek() returns the top item from the stack.
func (s *Stack) Peek() int {
    l := s.Size()
    return s.items[l-1]
}

// IsEmpty() tests to see whether the stack is empty and returns a boolean value.
func (s *Stack) IsEmpty() bool {
    return s.Size() == 0
}
```

### Decimal to any Base
![Decimal-to-Binary Conversion](../images/data-structures/dectobin.png)

```go
func baseConverter(decNumber int, base int) string {
	remStack := Queue{}
	for decNumber > 0 {
		rem := decNumber % base
		remStack.Push(rem)
		decNumber = decNumber / base
	}
	newString := ""
	for !(remStack.IsEmpty()) {
		newString = newString + strconv.Itoa(remStack.Pop())
	}
	return newString
}
```

### References
[Problem Solving with Algorithms and Data Structures using Python](https://runestone.academy/ns/books/published/pythonds/index.html)
