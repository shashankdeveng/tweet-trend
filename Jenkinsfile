pipeline {
    agent {
        node {
            label 'maven'
        }
    }
environment {
    PATH = "/opt/apache-maven-3.9.6/bin:$PATH"
}

    stages {
        stage("build"){
            steps {
                sh 'mvn clean deploy'
            }
        }

        stage("SonarQube analysis"){
        environment {
            scannerHome = tool 'shashank-sonar-scanner'
        }
            steps{
                withSonarQubeEnv('shashank-sonarqube-server')
                sh "${scannerHome}/bin/sonar-scanner"
            }
        }
    }
}