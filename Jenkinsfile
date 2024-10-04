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

        stage('Build Application') {
            steps{
                sh 'mvn clean package'
            }
        }

        stage('Test Application') {
            steps {
                sh 'mvn test'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                witSonarQubeEnv(credentialsId: 'jenkins-sonarqube') {
                    sh 'mvn sonar:sonar'
                }
            }
        }
    }
}