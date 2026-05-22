# Project 1.1 — Implementing Jenkins Pipeline as Code Using Jenkinsfile

## Tools Required

- Jenkins
- GitHub
- Git
- Java
- Maven
- Jenkinsfile

---

# Task 1 — Prepare GitHub Repository

## Step 1 — Create Repository

Repository Name:

```text
java-ci-demo
```

---

## Step 2 — Clone Repository

```bash
git clone https://github.com/YOUR_USERNAME/java-ci-demo.git
```

---

## Step 3 — Create Project Structure

```bash
mkdir -p java-ci-demo/src/main/java
cd java-ci-demo
```

Project Structure:

```text
java-ci-demo
│
├── src
│   └── main
│       └── java
│           └── App.java
│
├── pom.xml
└── Jenkinsfile
```

---

## Step 4 — Create Java File

File:

```text
src/main/java/App.java
```

Code:

```java
public class App {
    public static void main(String[] args) {
        System.out.println("Hello Jenkins Pipeline");
    }
}
```

---

## Step 5 — Create pom.xml

File:

```text
pom.xml
```

Code:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
         http://maven.apache.org/xsd/maven-4.0.0.xsd">

    <modelVersion>4.0.0</modelVersion>

    <groupId>com.demo</groupId>
    <artifactId>java-ci-demo</artifactId>
    <version>1.0</version>

    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>

</project>
```

---

# Task 2 — Create Jenkinsfile

## Step 1 — Create Jenkinsfile

File:

```text
Jenkinsfile
```

---

## Step 2 — Add Pipeline Code

```groovy
pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/YOUR_USERNAME/java-ci-demo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
    }
}
```

---

# Task 3 — Push Code to GitHub

## Step 1 — Initialize Git

```bash
git init
```

---

## Step 2 — Add Remote Repository

```bash
git remote add origin https://github.com/YOUR_USERNAME/java-ci-demo.git
```

---

## Step 3 — Add Files

```bash
git add .
```

---

## Step 4 — Commit Code

```bash
git commit -m "Initial Jenkins Pipeline Project"
```

---

## Step 5 — Push Code

```bash
git branch -M main
git push -u origin main
```

---

# Task 4 — Install Jenkins

## Step 1 — Install Java

```bash
sudo apt update
sudo apt install openjdk-17-jdk -y
```

---

## Step 2 — Install Jenkins

```bash
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
/usr/share/keyrings/jenkins-keyring.asc > /dev/null
```

```bash
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
/etc/apt/sources.list.d/jenkins.list > /dev/null
```

```bash
sudo apt update
sudo apt install jenkins -y
```

---

## Step 3 — Start Jenkins

```bash
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

---

# Task 5 — Access Jenkins

Open:

```text
http://SERVER_IP:8080
```

Get password:

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

---

# Task 6 — Create Jenkins Pipeline Job

## Step 1 — Create New Item

```text
New Item
```

---

## Step 2 — Enter Job Name

```text
java-ci-pipeline
```

Select:

```text
Pipeline
```

Click:

```text
OK
```

---

# Task 7 — Configure Pipeline

## Step 1 — Select Pipeline Script from SCM

```text
Pipeline script from SCM
```

---

## Step 2 — Select SCM

```text
Git
```

---

## Step 3 — Add Repository URL

```text
https://github.com/YOUR_USERNAME/java-ci-demo.git
```

---

## Step 4 — Add Branch

```text
*/main
```

---

## Step 5 — Add Script Path

```text
Jenkinsfile
```

---

## Step 6 — Save Job

```text
Save
```

---

# Task 8 — Run Pipeline

Click:

```text
Build Now
```

---

# Task 9 — Verify Pipeline

Check:

- Stage View
- Console Output
- Build Status
- Generated Artifact

---

# Expected Outcome

- Checkout stage executed
- Build stage executed
- Test stage executed
- Package stage executed
- Artifact generated successfully