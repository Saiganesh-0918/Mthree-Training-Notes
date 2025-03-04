# Linux Day 4

## **Regular Expressions (RegEx) in Linux**
Regular expressions are used to search and extract patterns in text files.

### **Extract Email IDs from Log Files**
```sh
grep -Eo '[a-zA-Z0-9._%+-]{3,}@[a-zA-Z0-9._]+\.[a-zA-Z]{2,}' sample-logs.md
```

### **Filter Requests Completed in More Than 1000ms**
```sh
grep -E "completed in [0-9]{4,}ms" sample-logs.md
```

### **Filter API Requests Based on Completion Time**
```sh
grep -E "API request completed in [0-9]+ms" sample-logs.md
```

## **Extracting and Sorting Data Using awk**
```sh
awk '{print $3}' sample-logs.md | sort | uniq -c  # Count unique values in column 3
awk '{print $3}' sample-logs.md | sort            # Sort values in column 3
```

## **Monitoring System Resources**
### **Extract CPU and Memory Usage**
```sh
grep -E "CPU usage: .*[7-9][0-9]%" sample-logs.md  # Find CPU usage above 70%
grep -Eo "Memory: [0-9]+%" sample-logs.md        # Extract memory usage
```

## **Installing Python in Ubuntu**
```sh
sudo apt update
sudo apt upgrade -y
sudo apt install -y python3-pip python-venv
python3 --version
pip3 --version
```

## **Installing Node.js in Ubuntu**
```sh
sudo apt install -y nodejs npm
sudo npm install -g @bazel/bazelisk
```

## **Additional Learnings**
- Practiced **log analysis using grep and awk**.
- Installed **Python and Node.js** on Ubuntu.
- Explored **Bazel package manager**.

### **Summary**
- Learned **RegEx filtering** using `grep`.
- Used **awk for data extraction and sorting**.
- Monitored system resources like **CPU, memory, and disk usage**.
- Installed **Python and Node.js** on Ubuntu for future development.
