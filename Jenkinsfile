pipeline {
    agent any
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
        stage('package') {
            steps {
                script {
                    // test
                    sh 'mvn package'
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


  
        

       
