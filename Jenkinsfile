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
       



    
    }
    }
