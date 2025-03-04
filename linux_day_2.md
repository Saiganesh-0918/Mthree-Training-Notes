# Linux Day 2

## **File and Directory Operations**
### **Removing Files and Directories**
```sh
rmdir -p directory_name  # Removes an empty directory
rm -rf file_name         # Deletes a file or directory forcefully
```

### **Getting Help with Commands**
```sh
man command_name  # View command manual (example: man rmdir)
```

## **System Information Commands**
```sh
uname -a  # Display complete system information
uname -r  # Show kernel release version
uname -s  # Display kernel name
uname -v  # Show kernel version
uname -m  # Display machine architecture
uname -p  # Show processor type
uname -i  # Display hardware platform
uname -o  # Show operating system name
```

## **Working with Files**
```sh
cat file_name         # View file content
ps aux                # List all running processes
kill -9 process_id    # Kill a specific process by its ID
whoami                # Display the current user
```

### **Sorting File Content**
```sh
sort -r file_name  # Sort in descending order
sort file_name     # Sort in ascending order
```

### **Word and Line Count**
```sh
wc -l file_name  # Count lines
wc -w file_name  # Count words
wc -c file_name  # Count characters
wc *             # Count files in a directory
```

## **Working with Calendar in Linux**
```sh
sudo apt install ncal  # Install calendar package
cal                    # Show current month's calendar
cal 2003               # Display calendar for a specific year
```

## **Useful Linux Commands**
```sh
history | grep text   # Search command history
alias l="ls -lrt"     # Create an alias for listing files
sudo apt install ncdu # Install ncdu package
ncdu .               # Show disk usage in current directory
echo "SAI GANESH" > file_name  # Write text into a file
```

## **Shell Scripting Basics**
```sh
vi one.sh         # Create a shell script
chmod 777 one.sh  # Grant execute permissions
./one.sh          # Run the script
```

### **Extracting Data from Files Using awk**
```sh
awk '{print $1}' data.txt  # Print first column
awk '{print $2}' data.txt  # Print second column
```

## **Compressing and Decompressing Files**
```sh
tar -cvf practice.tar a.text b.text  # Compress files
tar -xvf practice.tar               # Extract files
```

## **Additional Learnings**
- Practiced `awk` and conditional statements.
- Solved coding problems on HackerRank.

### **Summary**
- Learned file operations and process management.
- Explored shell scripting and data extraction using `awk`.
- Worked on compression and decompression using `tar`.
- Hands-on practice with Linux commands and shell scripting.
