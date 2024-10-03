pipeline {
    agent {
        node {
            label "maven-slave"
        }
    }
    environment {
        PATH = "/opt/apache-maven-3.9.9/bin:$PATH"
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean compile -e'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test -e'
            }
        }
        stage('Deploy') {
            steps {
                sh 'mvn deploy -e'
            }
        }
    }
}
