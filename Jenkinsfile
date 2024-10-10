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
                echo "--------Maven started-------"
                sh 'mvn clean deploy -Dmaven.test.skip=true'
                echo "--------Build completed---------------"
            }
        }
        stage('Test') {
            steps {
                echo "-------------unit test started---------"
                sh 'mvn surefire-report:report'
                echo "---------unit test completed"
            }
        }
        stage('SonarQube analysis'){
        environment {
           scannerHome = tool 'devop_sonar_scanner'; //sonar scanner name should be same as what we have defined on the jenkins tool.
        }

        steps {
        withSonarQubeEnv('sonarqube-server'){ // in this step we are adding our sonar qube server that is with sonar qube environment.
           sh "${scannerHome}/bin/sonar-scanner" // this is going to communicate with oue sonarqube server and send the analysis file.

        }
        } 



    
    }
    }
}