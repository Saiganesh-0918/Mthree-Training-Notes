LINUX(DAY-1)

Firstly we installed Linux on Windows with WSL. We are installing Linux in Windows with WSL because we can work on both Windows and Linux as per the requirement and in one machine.

### Installing WSL on Windows
```bash
wsl --install
```
- It will enable and install the features of the Ubuntu distribution.
- Next, setup the username and password.
- Now install MySQL in Ubuntu by using the below command.

```bash
sudo apt install mysql-server
```

To move to MySQL, we need to run the command:
```bash
sudo mysql
```

### Commands Executed in WSL
```bash
cd /mnt/c/  # Move to the C drive
ls -lrt  # Lists all the files in the current directory
mkdir Linux  # Creating a new Linux directory
cd LinuxPractise/  # Moving to the Linux directory
ls -lrt  # Should return empty
vi a.txt  # Opens a new file using the vi editor
ls -lrt  # Checking if the file is created
mkdir -p a/b/c/d/e/f/g/h/i/j/k/l/m/temp.txt  # Creating nested files
```

### Copy and Remove Commands
```bash
cp -rf b.txt /mnt/c/  # Copying b.txt file to C drive
cp -rf a /mnt/c/Users/username/  # Copies the entire folder and text
rm -rf /mnt/c/Users/srs33/a  # Deletes the entire file from the directory
```

### Permissions in Linux
Permissions are divided into three categories:
1. **Owner**
2. **Group**
3. **Others**

Each category has three types of permissions:
- Read (4)
- Write (2)
- Execute (1)

```bash
chmod -R 777 a  # Gives permission to all categories
```

### Grep Command
Grep is used to search for a word in the system.
```bash
grep -Ril "text"
```
- `R` - Recursive search
- `i` - Case insensitive
- `l` - Show file name instead of full content

For more details:
```bash
man grep
```

### Afternoon Session
- Brushed up on all the topics discussed in the morning.
- Resolved an issue with my laptop with the help of the trainer and friends.
- Solved a few basic Linux shell questions on HackerRank.

### **Summary**
- Installed and configured Linux on Windows using WSL.
- Worked with files and directories using Linux commands.
- Explored permissions and text searching using `grep`.
- Hands-on practice with shell scripting and problem-solving.
