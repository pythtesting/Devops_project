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
        stage('build') {
            steps {
                sh 'mvn clean deploy -X'
            }
        }
    }
}
