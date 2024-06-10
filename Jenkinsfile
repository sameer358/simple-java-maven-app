pipeline {
    agent any

    tools {
        maven 'Maven 3.9.0' // Ensure Maven is installed on Jenkins and configure it under Global Tool Configuration
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/sameer358/simple-java-maven-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml' // Publish test results
            archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
        }
    }
}
