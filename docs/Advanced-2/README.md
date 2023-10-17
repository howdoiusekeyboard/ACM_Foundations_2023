# ACM Foundations - Linked Lists, Stacks and Queues
# 1. Linked Lists
## 1.1 Why use Linked Lists?
Let us assume you are making a website and you need to record the names of customers who log in on the site. What size array would you use to store the data? If you select too small a size, then you will run out of space in the array. If you select a size too large you will be wasting space as much of it will be unused. It would be a lot more convenient if we could create a data-structure that could increase or decrease in size depending on how much data you wish to store in it. That is exactly what linked lists are designed for.

## 1.2 How do Linked Lists Work?
A linked list is made up of nodes, each node is a variable that keeps track of two values :
1. The value of the element in that node
2. A pointer to the next node in the list (NULL if it is the last node in the list)

The first node of the list is stored in a variable, generally termed 'head' or 'root'.
	![alt text](https://www.simplilearn.com/ice9/free_resources_article_thumb/Linked-List-Soni/representation-of-linked-list.png)
	
	
## 1.3 Linked List Implementation (Python 3.x)
First we need a node that can hold a value and the next node in the chain.

```python
class Node:
    def __init__(self, value = None):
        self.value = value
        self.next_ptr = None
```

Now let us make a simple class where we can add new elements to the list.
```python
class LinkedList:
    def __init__(self):
        self.root = None # no node when we create the list
        self.size = 0
    
    def insert_value(self, value):
        if self.root == None:
            self.root = Node(value)
            self.size += 1
            return
        
        curr_node = self.root
        while curr_node.next_ptr is not None:
            curr_node = curr_node.next_ptr

        curr_node.next_ptr = Node(value)
        self.size += 1
```

We can use this class to store email addresses of people who join the site as they come. This code will also print the number of elements in the list after it is created.
```python
emails = LinkedList()

while True:
    email_id = input("Enter an email id: ")
    if email_id == "":
        break
    
    emails.insert_value(email_id)

print("Number of email ids in the list:", emails.size)
```

If we want to print the elements in the list, we can copy the root and iterate over the list till we hit a null value.
```python
curr_node = emails.root

while curr_node is not None:
    print(curr_node.value)
    curr_node = curr_node.next_ptr
```

## 1.4 Problem : Number to Linked List
Take an integer as input and convert it to a linked list where each node is a digit of the number.

Note that if you try to simply insert the values into the list the number will end up reversed like this : 
```python
number = int(input("Enter a number: "))

ll = LinkedList()

while number != 0:
    digit = number % 10

    ll.insert_value(digit)

    number = int(number / 10)

curr_node = ll.root

while curr_node is not None:
    print(curr_node.value, end = " -> ")
    curr_node = curr_node.next_ptr
```

So to solve this issue we have two approaches : 
1. We create a function to insert an element at the start of a list rather than the end.
2. We reverse the list after creating it.

To implement code to add new elements to the start of the list, we can do something like this
```python
class LinkedList:
    def __init__(self):
        self.root = None # no node when we create the list
        self.size = 0
    
    def insert_value(self, value):
        if self.root == None:
            self.root = Node(value)
            self.size += 1
            return
        
        curr_node = self.root
        while curr_node.next_ptr is not None:
            curr_node = curr_node.next_ptr

        curr_node.next_ptr = Node(value)
        self.size += 1

    def insert_start(self, value):
        prev_root = self.root

        new_root = Node(value)
        new_root.next_ptr = prev_root

        self.root = new_root

number = int(input("Enter a number: "))

ll = LinkedList()

while number != 0:
    digit = number % 10

    ll.insert_start(digit)

    number = int(number / 10)

curr_node = ll.root

while curr_node is not None:
    print(curr_node.value, end = " -> ")
    curr_node = curr_node.next_ptr
```

## 1.5 Try it Yourself
Try writing the code to reverse the linked-list by yourself.


# 2. Stacks

## 2.1 What are Stacks?
Stacks are a data structure in which elements are inserted one after the other, and the most recent elements are removed first. For example, if we need to make a system where we analyze news articles and need to read the latest articles first before we look at old ones, stacks are perfect for this problem.

![alt text](https://cdn.programiz.com/sites/tutorial2program/files/stack.png)

A stack has two main operations that we need to perform : 
1. Push : Adds a value to the stack
2. Pop : Removes a value from the stack

Other common operations are :
1. Top : Returns the value at the top of the stack
2. Size : Returns the number of elements in the stack
3. IsEmpty : True if the stack is empty

## 2.2 Stack Implementation (Python 3.x)

```python
class Stack:
    def __init__(self):
        self.root = None # no node when we create the list
        self.size = 0
    
    def push(self, value):
        '''
        Adds a value to the top of the stack.
        '''
        if self.root == None:
            self.root = Node(value)
            self.size += 1
            return
        
        curr_node = self.root
        while curr_node.next_ptr is not None:
            curr_node = curr_node.next_ptr

        curr_node.next_ptr = Node(value)
        self.size += 1

    def pop(self):
        '''
        Removes a value from the top of the stack
        '''

        if self.root == None:
          return None

        elif self.size == 1:
          val = self.root.value
          self.root = None
          self.size = 0
          return val

        curr_node = self.root
        # loop to find the 2nd last element in the stack and put it in curr_node
        while curr_node.next_ptr.next_ptr is not None:
            curr_node = curr_node.next_ptr
        
        val = curr_node.next_ptr.value # val = last element in the stack
        curr_node.next_ptr = None # delete the last element
        self.size -= 1
        return val
    
    def top(self):
        '''
        Returns the value from the top of the stack
        '''

        if self.root == None:
          return None

        elif self.size == 1:
          val = self.root.value
          return val

        curr_node = self.root
        # loop to find the 2nd last element in the stack and put it in curr_node
        while curr_node.next_ptr.next_ptr is not None:
            curr_node = curr_node.next_ptr
        
        val = curr_node.next_ptr.value # val = last element in the stack
        return val

    def isEmpty(self):
        '''
        True if the stack is empty. False otherwise.
        '''
        return self.size == 0
```

## 2.3 Problem : Valid Brackets

Write a program to check if a series of brackets are valid. 
Ex. 
1. [()()] is valid
2. [} is invalid
3. [(] is invalid



```python
string = input("Enter the brackets: ")


def isValidBrackets(string):
    stack = Stack()

    for char in string:
        if char == '(' or char == '{' or char == '[':
            stack.push(char)
        elif char == ')':
            val = stack.pop()

            if val == '(': # correct opening bracket for this closing bracket
                continue
            else:
                return False
        elif char == ']':
            val = stack.pop()

            if val == '[': # correct opening bracket for this closing bracket
                continue
            else:
                return False
        elif char == '}':
            val = stack.pop()

            if val == '{': # correct opening bracket for this closing bracket
                continue
            else:
                return False

    if stack.isEmpty(): # no remaining open brackets should be left in the stack
        return True
    else:
        return False
    

if isValidBrackets(string):
    print("Valid brackets.")
else:
    print("Invalid brackets.")
```

# 3. Leetcode

## 3.1 Introduction to Leetcode
[Leetcode](https://leetcode.com/) is currently the largest online platform where you can learn and practice coding interview style questions. These types of questions are largely based on data structures and algorithms and are also commonly seen in competitive programming contests.
## 3.2 Your First Problem
Let us try leetcode out with the above stack problem. [Valid Parentheses](https://leetcode.com/problems/valid-parentheses/) is an easy leetcode problem. Try pasting your solution to the problem from the code above and see the results! Keep in mind that as this code is not optimized, the execution speed will not be competitive. Try re-writing the code using native python lists to improve performance.









