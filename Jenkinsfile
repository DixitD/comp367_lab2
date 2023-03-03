//Jenkinsfile (Declarative Pipeline)
/* Requires the Docker Pipeline plugin */
pipeline {
    agent  any   
    stages {
        stage('build') {
            steps {
                withMaven(maven: 'maven3') {
                sh 'mvn clean package'
            }
        }
    }
}
}
