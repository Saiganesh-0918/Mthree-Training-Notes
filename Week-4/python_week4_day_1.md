# Python Week-4 Day-1

## **Python Problem-Solving**
After building a basic understanding of Python, we worked on solving coding challenges.

### **Navigating to Project Directory**
```sh
cd ~/basic-module  # Move to the project directory
```

### **Problem 1: Reverse Words in a String**
#### **Input:**
```sh
"My name is Sai Ganesh"
```
#### **Output:**
```sh
"Ganesh Sai is name My"
```
#### **Code:**
```python
def reverse_words(s):
    words = [word for word in s.split() if word]
    return ' '.join(words[::-1])

print(reverse_words("My name is Sai Ganesh"))
```

### **Problem 2: Find Largest Odd Number from Given Number**
#### **Test Cases:**
```sh
Input: 51  -> Output: 51
Input: 52  -> Output: 5
Input: 35428 -> Output: 35
```
#### **Code:**
```python
def largest_odd_numbers(s):
    for i in range(len(s)-1, -1, -1):
        if int(s[i]) % 2 == 1:
            return s[:i+1]
    return ""

print(largest_odd_numbers("51"))
print(largest_odd_numbers("52"))
print(largest_odd_numbers("35428"))
```

### **Problem 3: Check if a String is a Rotation of Another**
#### **Test Cases:**
```sh
Input: "abcde", "cdeab"  -> Output: True
Input: "abcde", "cdeba"  -> Output: False
```
#### **Code:**
```python
s1 = "abcde"
s2 = "cdeab"
print(len(s1) == len(s2) and s2 in (s1 + s1))
```

### **Additional Learning**
- Explored the **LMS portal**.
- Discussed and **finalized a project with the trainer**.

## **Summary**
- Solved Python coding challenges.
- Practiced **string manipulations** and **number operations**.
- Explored **project ideas for implementation**.
