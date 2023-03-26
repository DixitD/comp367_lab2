pipeline {
    agent any
    environment {
        DOCKERHUB_PWD=credentials('Docker_Hub_Password')
        DOCKERHUB_USERNAME=credentials('Docker_Hub_Username')
    }
    stages {
        stage('Maven Build') {
            steps {
                withMaven(maven: 'maven3') {
                sh 'mvn clean package'
                }
            }
        }
        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${DOCKERHUB_USERNAME}/webapp:latest ."
            }
        }
        stage('Docker Login')
        {
            steps {
                script {
                    sh 'docker login -u ${DOCKERHUB_USERNAME} -p ${DOCKERHUB_PWD}'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                sh "docker push ${DOCKERHUB_USERNAME}/webapp:latest"
            }
        }
    }
}


