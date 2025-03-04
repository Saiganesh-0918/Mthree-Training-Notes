# Python Day 1

## **Conditional Statements in Python**
### **If-Else Condition**
```python
age = int(input("Enter your age: "))
if age >= 18:
    print("You are eligible to vote.")
else:
    print("You are not eligible to vote.")
```

## **Loops in Python**
### **For Loop**
```python
for i in range(1, 4):
    print(i)

for letter in "Python":
    print(letter)
```

### **While Loop**
```python
age = int(input("Enter your age: "))
while age < 0:
    print("Invalid age. Please enter again.")
    age = int(input("Enter your age: "))
print("Valid age entered.")
```

## **Functions in Python**
```python
def greet(name):
    return f"Hello, {name}!"

name = input("Enter your name: ")
print(greet(name))
```

## **Building Python Packages Using Wheel**
```sh
mkdir -p src/basic_module/datastructure
cd src/basic_module/datastructure

# Create Python module
cat > pattern.py
cd ../../..
touch src/basic_module/__init__.py
cd src/basic_module/
touch __init__.py
touch datastructure/__init__.py
echo "# Basic Module" > README.md
```

## **Installing and Running Python Package**
```sh
python3 -m build --wheel
pip install dist/basic_module-0.1.0-py3-none-any.whl --force-reinstall
```

## **Additional Learnings**
- Explored **pyproject.toml** for build configurations.
- Practiced **packaging and installing Python modules**.
- Solved Python coding problems.

### **Summary**
- Learned **if-else conditions** and **loops (for, while)**.
- Worked with **functions and user input handling**.
- Explored **Python package building using wheel**.
- Practiced **coding challenges and quizzes**.
