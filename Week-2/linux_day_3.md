# Linux Day 3

## **Shell Scripting & Conditional Statements**

### **Working with Arrays in Shell Scripting**
```sh
vi array.sh          # Create a shell script file
chmod 777 array.sh   # Grant execute permissions
./array.sh           # Execute the script
```

### **Printing Array Elements**
```sh
echo "${a[@]}"  # Prints all elements of the array
```

## **Using Conditional Statements**

### **Check if a String is Empty**
```sh
if [ -z "$description" ]; then
    echo "String is empty"
else
    echo "String is not empty"
fi
```

## **Taking User Input in Shell Scripting**
```sh
read -p "Enter your name: " username  # Takes user input
```

### **Hiding Password Input**
```sh
read -s -p "Enter your password: " password  # Hides user input for security
```

## **Using Case Statements in Shell Scripts**
```sh
case "$choice" in
    1) echo "Option 1 selected" ;;
    2) echo "Option 2 selected" ;;
    *) echo "Invalid option" ;;
esac
```

## **Searching Text Using grep Command**
```sh
grep "s.lection$" case.sh   # Finds lines ending with 'lection'
grep "^s" case.sh           # Finds words starting with 's'
grep "[a-zA-Z]" case.sh    # Finds words with uppercase and lowercase letters
grep "s*a" case.sh         # Finds words containing 's' and 'a'
```

## **Additional Learnings**
- Practiced searching text with `grep` across multiple files.
- Explored security features like hidden password input.
- Solved shell scripting challenges and quizzes.

### **Summary**
- Learned **arrays and loops** in shell scripting.
- Explored **conditional statements and case statements**.
- Worked with **grep** for text searching.
- Hands-on practice with **interactive shell scripting**.
