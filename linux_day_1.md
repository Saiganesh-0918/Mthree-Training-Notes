# Linux Day 1

## **Installing Linux on Windows using WSL**
WSL (Windows Subsystem for Linux) allows us to use Linux on Windows.

### **Installation Steps:**
```sh
wsl --install
```
- This enables and installs Ubuntu distribution.
- Set up a username and password.
- Install MySQL in Ubuntu:
  ```sh
  sudo apt install mysql-server
  ```
- To enter MySQL:
  ```sh
  sudo mysql
  ```

## **Basic Linux Commands:**
### **Navigating Directories**
```sh
cd /mnt/c/          # Move to C drive
ls -lrt             # List all files in the current directory
mkdir Linux         # Create a new Linux directory
cd LinuxPractise/   # Move to the Linux directory
```

### **Creating Files and Directories**
```sh
vi a.txt              # Create and open a new file using vi editor
touch c406.txt        # Create a file using touch command
touch {1..5}.txt      # Create multiple files at once
```

### **Copying and Removing Files**
```sh
cp -rf b.txt /mnt/c/                    # Copy b.txt to C drive
cp -rf a /mnt/c/Users/username/          # Copy entire folder
rm -rf /mnt/c/Users/srs33/a              # Delete a directory
```

## **Linux File Permissions**
Each file has three permission categories:
1. **Owner**
2. **Group**
3. **Others**

| Permission | Read | Write | Execute |
|------------|------|-------|---------|
| **Value**  | 4    | 2     | 1       |

### **Modifying Permissions**
```sh
chmod -R 777 a  # Gives full permissions to all users
```

## **Searching in Linux**
The `grep` command is used to search for text in files.
```sh
grep -Ril "text"    # Search for 'text' in all files recursively
man grep            # Get detailed documentation on grep
```

## **Additional Learnings**
- **Worked on Linux shell questions on HackerRank**
- **Troubleshooting WSL installation issues with trainer and friends**

### **Summary**
- Installed and configured Linux on Windows using WSL.
- Worked with files and directories using Linux commands.
- Explored permissions and text searching using `grep`.
- Hands-on practice with shell scripting and problem-solving.
