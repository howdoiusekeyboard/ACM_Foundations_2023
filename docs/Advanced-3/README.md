# ACM Foundations - Hash Sets and Hash Maps
# 1. Hash Sets
## 1.1 What are hash sets?
Imagine you are making a website with millions of users. Whenever a user wishes to login in to the site you will need to check if his username is in the database and then check if his password matches the one for his account. But if we have so many users then checking an array or a list with all users for this username will be very time consuming. Hash sets are a data structure that allow you to lookup a value in a very short amount of time regardless of how many elements there are.

## 1.2 Problem Statement
Let us tackle a simple version of this problem first. Can we make a program that can tell you if an element is in an array that takes a constant amout of time to run regardless of the array's size? 

## 1.3 Basic Solution
Well, let us first think of what operations will take the same amount of time to run regardless of the input size :
1. Arithmetic Operations (+, -, *, /, %)
2. Indexing Elements in an Array (arr[i])
3. Logical Expressions (<, >, ==, !=)
4. If-Else Conditions

What if we try writing a program where we have a function ind(x) that returns the expected location of an element in an array? Then this function could take as input an element x, check if the element is present at that index in the array. The way we do this is to create an array of booleans and set the value at that index to True if the element is present. Also we will name the function that returns indices our hash_function.

Let us look at a simple code for a hash set that stores elements between 0 and 9.

```python
def hash_function(x, arr_size):
    index = x % arr_size

    return index

arr_size = 10

hash_set = [False] * arr_size

input_elements = [1, 2, 5, 8]

for ele in input_elements:
    ind = hash_function(ele, arr_size)

    hash_set[ind] = True


# User input
while True:
    new_element = int(input("Enter a number between 0 and 9 : "))

    if new_element == -1:
        break
    
    ind = hash_function(new_element, arr_size)

    if hash_set[ind] == True:
        print("Element is present in the set.")
    else:
        print("Element is not present in the set.")
```

## 1.4 Expanding Hash Sets
What if we have an almost infinite input scope (like usernames)? Then we will have collisions where many elements are all mapped to the same index. To accommodate this, we will create an array of linked-lists and to store an element we will insert it into the linked list at that position. Keep in mind that this is still much faster than using a single linked list to store all our values.

![alt text](https://i.stack.imgur.com/enJhc.png)


Let us now make a hash set to store any positive integer.

```python
def hash_function(x, arr_size):
    index = x % arr_size

    return index

def insert_ele(hash_set, ele, arr_size):
    index = hash_function(ele, arr_size)

    hash_set[index].append(ele)

def is_present(hash_set, ele, arr_size):
    index = hash_function(ele, arr_size)

    linked_list = hash_set[index]
  
    for i in range(len(linked_list)):      
        if linked_list[i] == ele:
          return True
    
    return False

arr_size = 100

hash_set = [[].copy() for i in range(arr_size)]

input_elements = [50, 90, 1000, 2000]

for ele in input_elements:
    insert_ele(hash_set, ele, arr_size)


# User input
while True:
    new_element = int(input("Enter a number: "))

    if new_element == -1:
        break
    
    if is_present(hash_set, new_element, arr_size):
        print("Element is present in the set.")
    else:
        print("Element is not present in the set.")
```

## 1.4 Efficient Python Implementation
To use hash sets efficiently in python, there is the built-in set datatype. Let us see the speed increase of this class over a python list. 

```python
import time

limit = 10 ** 7

nums = range(limit)

lst = list(nums)
hash_set = set(nums)

start = time.time()
print(limit in lst)
print("The list took {} seconds to search though the whole list.".format(time.time() - start))

start = time.time()
print(limit in hash_set)
print("The set took {} seconds to search though the whole list.".format(time.time() - start))
```


# 2. Hash Map

## 2.1 Extending Hash Sets
A hash set can only be used to find if an element is in an array. What if we need to find some associated value for that element? For example, in a website we will need to link the username to a password. This is where hashmaps come in, these are called mappings as they map some input to a fixed value.

![alt text](https://miro.medium.com/v2/resize:fit:554/0*TaC2P062slR3GugM.png)

We can do this by making each entry in the linked-lists hold two values, the first value will be the key and the second one will be the data we are storing. Let us look at an example with user ids and passwords.

```python
def hash_function(usr_id, arr_size):
    index = usr_id % arr_size

    return index

def insert_usr(hash_map, usr_id, password, arr_size):
    index = hash_function(usr_id, arr_size)

    hash_map[index].append((usr_id, password))

def is_usr_present(hash_map, usr_id, arr_size):
    index = hash_function(usr_id, arr_size)

    linked_list = hash_map[index]
  
    for i in range(len(linked_list)):      
        if linked_list[i][0] == usr_id: # index 0 is the user_id in a list entry
          return True
    
    return False

def get_password(hash_map, usr_id, arr_size):
    index = hash_function(usr_id, arr_size)

    linked_list = hash_map[index]
  
    for i in range(len(linked_list)):      
        if linked_list[i][0] == usr_id: # index 0 is the user_id in a list entry
          return linked_list[i][1] # password for that user
    
    return None

arr_size = 100

hash_map = [[].copy() for i in range(arr_size)]

input_users = [(12, "pass"), (10, "abcd"), (10016, "12345"), (190903, "adJn%^0")]

for info in input_users:
    usr_id, password = info
    insert_usr(hash_map, usr_id, password, arr_size)

# User input
while True:
    new_user = int(input("Enter a user ID: "))

    if new_user == -1:
        break
    
    if is_usr_present(hash_map, new_user, arr_size) == False:
        print("This user is not present in the database.")
        continue

    stored_pass = get_password(hash_map, new_user, arr_size)

    entered_pass = input("Enter the password: ")

    if stored_pass == entered_pass:
        print("User authenticated!")
    else:
      print("Invalid password. Access denied.")
```

## 2.2 Efficient Python Implementation
Much like hash sets, python has an in-built class for hash maps called dictionaries. Let us re-write the above code using them.

```python
hash_map = dict()

input_users = [(12, "pass"), (10, "abcd"), (10016, "12345"), (190903, "adJn%^0")]

for info in input_users:
    usr_id, password = info
    hash_map[usr_id] = password

# User input
while True:
    new_user = int(input("Enter a user ID: "))

    if new_user == -1:
        break

    user_is_present = (new_user in hash_map)
    
    if user_is_present == False:
        print("This user is not present in the database.")
        continue

    stored_pass = hash_map[new_user]

    entered_pass = input("Enter the password: ")

    if stored_pass == entered_pass:
        print("User authenticated!")
    else:
      print("Invalid password. Access denied.")
```


# 3. Leetcode Problems

## 3.1 Easy Problem
[2283. Check if Number Has Equal Digit Count and Digit Value](https://leetcode.com/problems/check-if-number-has-equal-digit-count-and-digit-value/)

(Easy)

You are given a **0-indexed** string `num` of length `n` consisting of digits.

Return `true` *if for **every** index* `i` *in the range* `0 <= i < n`*, the digit* `i` *occurs* `num[i]` *times in* `num`*, otherwise return* `false`.

**Example 1:**

**Input:** num = "1210"
**Output:** true
**Explanation:**
num[0] = '1'. The digit 0 occurs once in num.
num[1] = '2'. The digit 1 occurs twice in num.
num[2] = '1'. The digit 2 occurs once in num.
num[3] = '0'. The digit 3 occurs zero times in num.
The condition holds true for every index in "1210", so return true.

**Example 2:**

**Input:** num = "030"
**Output:** false
**Explanation:**
num[0] = '0'. The digit 0 should occur zero times, but actually occurs twice in num.
num[1] = '3'. The digit 1 should occur three times, but actually occurs zero times in num.
num[2] = '0'. The digit 2 occurs zero times in num.
The indices 0 and 1 both violate the condition, so return false.

**Constraints:**

- `n == num.length`
- `1 <= n <= 10`
- `num` consists of digits.



**Logic**

Here we have to note down a few things:

1. The keys of the hashmap are 0- length of the string "num"

2. the occurence of each key is checked in the number. Accordingly the value to the Key is assigned.
   
   E.g: For the number "1210"
   
   num[0] = '1'. The digit 0 occurs once in num.
   num[1] = '2'. The digit 1 occurs twice in num.
   num[2] = '1'. The digit 2 occurs once in num.
   num[3] = '0'. The digit 3 occurs zero times in num.
   The condition holds true for every index in "1210", so return true.

3. To get the result "True": value assigned to each key in hashmap , should match the digit at the key index in number. e.g  for the number "1210"
   
   Hash Map 
   
   | Key | Values |     | Number | Digit |
   | --- | ------ | --- | ------ | ----- |
   | 0   | 1      |     | num[0] | 1     |
   | 1   | 2      |     | num[1] | 2     |
   | 2   | 1      |     | num[2] | 1     |
   | 3   | 0      |     | num[3] | 0     |

4. The "0"s in the beginning of the number are counted e.g- the number "030" has 2 zeros

code:

```python
class Solution(object):
    def digitCount(self, num):
        record_check = {}

        original_number = [0] * len(num)

        for i in range(len(num)):
            record_check[i] = 0

        for i in range(len(num)):
            ch = int(num[i])
            original_number[i] = ch
            if ch in record_check:
                count = record_check[ch]
                record_check[ch] = count + 1

        for i in range(len(num)):
            if original_number[i] != record_check[i]:
                    return False

        return True
```

## 3.2 Medium problem

[1930. Unique Length-3 Palindromic Subsequences](https://leetcode.com/problems/unique-length-3-palindromic-subsequences/)

(Medium)

Given a string `s`, return *the number of **unique palindromes of length three** that are a **subsequence** of* `s`.

Note that even if there are multiple ways to obtain the same subsequence, it is still only counted **once**.

A **palindrome** is a string that reads the same forwards and backwards.

A **subsequence** of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

- For example, `"ace"` is a subsequence of `"<u>a</u>b<u>c</u>d<u>e</u>"`.

**Example 1:**

**Input:** s = "aabca"
**Output:** 3
**Explanation:** The 3 palindromic subsequences of length 3 are:

- "aba" (subsequence of "<u>a</u>a<u>b</u>c<u>a</u>")
- "aaa" (subsequence of "<u>aa</u>bc<u>a</u>")
- "aca" (subsequence of "<u>a</u>ab<u>ca</u>")

**Example 2:**

**Input:** s = "adc"
**Output:** 0
**Explanation:** There are no palindromic subsequences of length 3 in "adc".

**Example 3:**

**Input:** s = "bbcbaba"
**Output:** 4
**Explanation:** The 4 palindromic subsequences of length 3 are:

- "bbb" (subsequence of "<u>bb</u>c<u>b</u>aba")
- "bcb" (subsequence of "<u>b</u>b<u>cb</u>aba")
- "bab" (subsequence of "<u>b</u>bcb<u>ab</u>a")
- "aba" (subsequence of "bbcb<u>aba</u>")

**Constraints:**

- `3 <= s.length <= 105`
- `s` consists of only lowercase English letters.

**Logic:**

Let's take the string "bbcbaba""

We need 3 values:

**1. First occurence of a character:** The first index position of the character 

**2. Last occurence of a character**: The last index postition of the character. If the character occurse only once, then the first index and last index of the character is same.

To keep track of characters and their index values, we use HashMaps since the character {keys} should be unique and their index position {value} should be stored with respect to the particular character

*NOTE: Since this is a key, value pair, we use the dictionary datatype in python.*

**3. Unique Characters:** The number of characters present in between the first and the last index. 

Note: the character must be unique, since palindromes of repeated letters would be counted as one.

E.g: "bbb" formed by "b"s at 0th,1st and 5th index is the same as "bbb" formed by "b"s at 0th,2nd and 5th index.

Hence to maintain the uniqueness of characters we use HashSet

*NOTE: To maintain the uniqueness we use the Set datatype in python.*

| Character | First Occurrence | Last Occurrence | Unique Characters Count (t) | Palindromes Count (a) |
| --------- | ---------------- | --------------- | --------------------------- | --------------------- |
| 'a'       | 4                | 6               | 1{b}                        | 1                     |
| 'b'       | 0                | 5               | 3{a,b,c}                    | 3                     |
| 'c'       | 2                | 2               | 0                           | 0                     |

code:

```python
class Solution(object):
    def countPalindromicSubsequence(self, s):
        total_palindromes = 0
        ch = list(s)
        first_occurrence = {}
        last_occurrence = {}

        for i, value in enumerate(ch):
            if value in first_occurrence:
                last_occurrence[value] = i
            else:
                first_occurrence[value] = i
                last_occurrence[value] = i

        for key in first_occurrence.keys():
                start = first_occurrence[key]
                end = last_occurrence[key]

                if end - start > 1:
                    between = set(ch[start+1:end])
                    total_palindromes += len(between)            
        return total_palindromes
```


