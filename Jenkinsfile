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

        stage('Deploy to Tomcat') {
            steps {
                script {
                    // Deploy the WAR file to Apache Tomcat using the Tomcat Manager API
                    sh """
                        curl -v -u ${tomcat}:${s3cret} \
                        "${TOMCAT_SERVER}/manager/text/deploy?path=/your-web-app&update=true" \
                        --upload-file target/your-web-app.war
                    """
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
