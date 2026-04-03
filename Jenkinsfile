pipeline {
    agent { label 'Jenkins-Agent' }
        tools {
            jdk 'java-17'
            maven 'maven-3'
        }
    
    stages {
        stage('Cleanup Workspace') {
            steps {
                // Clean the workspace before starting
                cleanWs()
            }
        }

        stage('Checkout from SCM') {
            steps {
                // Explicit Git checkout from repo and branch
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/LakshmiPrasannaMuppuri/Deploy-to-Kubernetes-Using-Jenkins.git'
            }
        } 

      stage('Build Application') {
            steps {
                echo "Building project with Maven..."
                sh 'mvn clean package'
            }
        }

      stage('Test Application') {
            steps {
                echo "Running tests..."
                sh 'mvn test'
            }
        }
    } 
}
