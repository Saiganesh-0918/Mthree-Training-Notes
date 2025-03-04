# Jenkins Day 1

## **Introduction to Jenkins**
Jenkins is an automation server used for **Continuous Integration (CI) and Continuous Deployment (CD)**. It automates the process of building, testing, and deploying applications.

## **Setting Up a Jenkins Project**
### **Creating a Directory and Initializing Git**
```sh
mkdir my_python_project
cd my_python_project
git init
```

### **Creating Project Files**
```sh
touch pyproject.toml   # Stores project dependencies
mkdir src tests        # Source and test directories
```

## **Setting Up Docker in the Project**
```sh
touch Dockerfile .gitignore
```
- **Dockerfile**: Defines how the container is built.
- **.gitignore**: Prevents unnecessary files from being committed.

### **Installing Build Tools**
```sh
pip install build
python3 -m build --wheel
```

## **Configuring Git**
```sh
git config --global user.email "your-email@example.com"
git config --global user.name "your-github-username"
git commit -m "Initial project setup with Python code and Dockerfile"
```

## **Creating a Jenkins Pipeline**
### **Creating a Jenkinsfile**
```sh
vi Jenkinsfile
```
A **Jenkinsfile** defines the CI/CD pipeline.

### **Pushing to GitHub**
```sh
git push -u origin main
```

## **Working with Jenkins**
1. Login to **Jenkins Dashboard**: `http://localhost:8080`
2. Use **admin** as username and the generated password.
3. Create a **New Item** → Select **Pipeline** → Configure **Jenkinsfile**.
4. Click **Build Now** to run the pipeline.
5. Check **Console Output** for logs.

## **Integrating Jenkins with GitHub**
1. Add **GitHub Repository URL** in Jenkins Pipeline settings.
2. Enable **SCM Polling** or **Webhooks** for automatic builds.

## **Summary**
- Installed and set up Jenkins.
- Created a **Jenkinsfile** for CI/CD automation.
- Configured Git and pushed project files to GitHub.
- Ran Jenkins builds and checked output logs.
- Explored integration between Jenkins and GitHub.
