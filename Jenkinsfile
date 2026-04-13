pipeline {
    agent any

    tools {
        maven 'MyMaven'   // must match Jenkins tool name
        jdk 'MyJDK'       // must match Jenkins JDK name
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Verify Build') {
            steps {
                sh 'ls -l target'
            }
        }
    }

    post {
        success {
            echo '✅ Guava Project Build Successful!'
        }
        failure {
            echo '❌ Guava Project Build Failed!'
        }
        always {
            echo '📌 Pipeline execution completed'
        }
    }
}
