# PYTHON (WEEK-4, DAY-5)

## OOPS Concepts in Python

### Method Overriding
- Method overriding is known as overriding the previous method.
- In technical terms, the method in the child class overrides the method in the parent class.
- The functionality remains the same, but the method is overridden with its own style.
- The main use of method overriding is to allow child classes to provide their own behavior for a method defined in the parent class.

### Method Overloading
- Python does not support method overloading like other programming languages.
- Method overloading is defined as the same method with different parameters.
- In Python, method overloading can be achieved using `*args`.
- It allows flexibility in how methods are called with parameters.

### Encapsulation
- Hiding unnecessary details and providing necessary details to the user.
- In Python, private members are created using a double underscore `__`.
- It protects sensitive data from direct modification and provides controlled access.

## Flow of Execution

### Example 1
1. Declared the parent class `Animal`:
   - The `__init__` method initializes the `name` attribute.
   - The `__str__` method returns a string representation of an object.
   - The `speak` method prints a message.
2. Declared the child class `Dog` inheriting from `Animal`:
   - Method overriding is applied to change the behavior of `speak()`.
   - Implemented method overloading (though Python does not support it directly).
   - The additional method `speak(self, age, name)` takes two arguments.
3. Declared additional child classes `Cat` and `Bird`, both overriding `speak(self)`.

### Example 2
- Correct implementation of method overloading by using default values for parameters.
- Difference:
  - `speak(self, age=0)` allows calling the method with or without arguments.
  - Previously, `speak(self, age)` required an argument, leading to errors.
  - The previous code used `print` while the updated version uses `return`, avoiding `None` output.

## Destructor
- A destructor is a special method in Python that is automatically called when an object is deleted or goes out of scope.
- The destructor `__del__()` runs automatically when an object is deleted.

### Flow of Execution
1. Defined the class `Resource`.
2. The constructor `__init__` prints a message when an object is created.
3. The destructor `__del__` runs when an object is deleted.
4. Created a function to demonstrate destruction:
   - Prints "Starting program".
   - Creates three resource objects (`Database Connection`, `File Handle`, `Network Connection`).
   - Destructor automatically destroys objects when the function ends.

## Shallow Copy vs Deep Copy
### Shallow Copy
- Creates a new object but does not create copies of nested objects.
- If the original object contains references to other objects, the copy will still point to the same objects.
- Any change in nested objects will affect both copies.

### Deep Copy
- Creates a completely independent object, including copies of all nested objects.
- Changes to the original object do not affect the deep copy.

### Flow of Execution
1. Defined two classes: `Person` and `Address`.
2. `Person` class contains a `name` string and an `address` object.
3. `Address` class has `city` and `country` attributes.
4. Used `__repr__()` for readable string representation.
5. Created objects for both classes.
6. Created a shallow copy:
   - The `shallow_person` object points to the same `address` object as `person.address`.
7. Created a deep copy:
   - The `deep_person` object has an independent `address` object.
8. Verified object IDs:
   - `shallow_person` is a new object but shares the same address as `person`.
   - `deep_person` has a separate address.
9. Changes in `person.address` reflect in `shallow_person` but not in `deep_person`.

## Exception Handling
### Try-Except-Finally
- **Try**: Contains the code we want to execute.
- **Except**: Catches errors if something goes wrong.
- **Finally**: Runs regardless of whether an exception occurs.

### Flow of Execution
1. Defined a custom exception class extending `Exception`.
2. Used `super()` to pass a message to the parent `Exception` class.
3. Used `raise` to manually trigger `CustomException` inside a `try` block.
4. The first `except` block catches `CustomException` and prints the message.
5. The second `except` block is not executed since the first one catches the exception.
6. The `finally` block always executes, regardless of an exception.

## File Operations
Performed file operations in Python using simple code:
- Created a file.
- Wrote to the file.
- Read from the file.
- Appended text to the file.
- Deleted the file.

In the breakout session, we reviewed the covered topics and discussed the final project along with LMS concepts.

