pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Fetching source code'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Compiling Maven Project'
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Tests'
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo 'Creating JAR'
                sh 'mvn package'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar'
            }
        }
    }

    post {
        success {
            echo 'Build Successful'
        }

        failure {
            echo 'Build Failed'
        }
    }
}