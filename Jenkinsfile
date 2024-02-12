pipeline {
    agent any

    environment {
        TOMCAT_SERVER = 'http://3.147.43.44:8070/'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build the WAR file using Maven
                    sh 'mvn clean install'
                }
            }
        }

        stage('test') {
            steps {
                script {
                    // test
                    sh 'mvn test'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline succeeded. Additional success steps can be added.'
        }
        failure {
            echo 'Pipeline failed. Additional failure steps can be added.'
        }
    }
}
