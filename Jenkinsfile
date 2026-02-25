pipeline {
    agent any
    tools {
        gradle 'Gradle' // Ensure this matches Jenkins tool config
        jdk 'JDK17'       // Ensure this matches Jenkins tool config
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/akshai-cs/Gradle-App.git'
            }
        }
        stage('Build') {
            steps {
                sh 'gradle build' // Run Gradle build
            }
        }
        stage('Test') {
            steps {
                sh 'gradle test' // Run unit tests
            }
        }
        stage('Run Application') {
            steps {
                // Option 1: If using Gradle application plugin
                sh 'gradle run'
                
                // Option 2: If you want to run the JAR directly
                // sh 'java -jar build/libs/Gradle-App-1.0.jar'
            }
        }
    }
    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}

