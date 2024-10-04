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
        stage('SonarQube analysis'){
        environment {
            scannerHome = tool 'devops-sonar-scanner'; //sonar scanner name should be same as what we have defined on the jenkins tool.
        }
        steps { withSonarQubeEnv('sonarqube-server'){ // in this step we are adding our sonar qube server that is with sonar qube environment.
                       sh "${scannerHome}/bin/sonar-scanner"  // this is going to communicate with oue sonarqube server and send the analysis file.
                   }
                   }

    }
}
