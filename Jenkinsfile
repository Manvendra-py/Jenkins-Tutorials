pipeline {
    agent any

    tools {
        jdk 'Java17'
        maven 'Maven3'
    }

    stages {
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
            }
        }

        stage('Ckeckout SCM') {
            steps {
                git branch: 'complete-prodcution-e2e-pipeline', credentialsId: 'github', url : 'https://github.com/Manvendra-py/Jenkins-Tutorials.git'
            }
        }
    }
}