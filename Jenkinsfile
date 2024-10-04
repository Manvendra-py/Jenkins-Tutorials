pipeline {
    agent any

    tools {
        jdk 'Java17'
        maven 'Maven3'
    }

    environmen {
        APP_NAME = 'complete-prodcution-e2e-pipeline'
        RELEASE = '1.0.0'
        DOCKER_USER = 'Manavendra'
        DOCKER_PASS = 'jenkins-dockerhub-token'
        IMAGE_NAME = '${DOCKER_USR}' + '/' + '${APP_NAME}'
        IMAGE_TAG = '${RELEASE}-${BUILD_NUMBER}'
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
                script {
                    withSonarQubeEnv(credentialsId: 'sonarqube-token') {
                        sh 'mvn sonar:sonar'
                    }
                }
            }
        }

        stage("Quality Gate") {
            steps {
                script {
                    wiatForQualityGate abortPipeline: false, credentialsId: 'sonarqube-token'
                }
            }
        }

        stage ('Build and Push Dcoker Image') {
            steps {
                script {
                    docker.withRegistry('',DOCKER_PASS) {
                        docker_image = docker.build '${IMAGE_NAME}'
                    }

                    docker.withRegistry('',DOCKER_PASS) {
                        docker_image.push('$IMAGE_TAG')
                    }
                }
            }
        }
    }
}