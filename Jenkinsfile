pipeline {
    agent any
    
        environment {
        DOCKER_REGISTRY = 'your-docker-registry'
        DOCKER_REGISTRY_CREDENTIALS_ID = 'your-docker-registry-credentials-id
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
         stage('Build and Push Docker Image') {
            steps {
                script {
                    // Build Docker image
                    docker.withRegistry('https://' + DOCKER_REGISTRY, 'docker-registry-credentials-id') {
                        def customImage = docker.build('your-docker-image-name:latest')

                        // Push Docker image to registry
                        customImage.push()
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


  
        

       
