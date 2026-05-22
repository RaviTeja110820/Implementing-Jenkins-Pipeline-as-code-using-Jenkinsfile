pipeline {

    agent any
    
    // agent any:
    // Jenkins can run this pipeline on ANY available executor/agent
    // If no other agents are configured, it runs on the Jenkins EC2 machine itself

    tools {
        maven 'mymaven'
    }
    // 'mymaven' must match the Maven name configured in:
    // Manage Jenkins → Tools → Maven installations

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/RaviTeja110820/Implementing-Jenkins-Pipeline-as-code-using-Jenkinsfile.git'
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
