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
        stage('build') {
            steps {
                sh 'mvn clean deploy'
            }
        }

        stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'sonar-scanner'
            }
            steps{
                withSonarQubeEnv(credentialsId: 'sonar-cred1', installationName: 'sonarqube-server') { // You can override the credential to be used, If you have configured more than one global server connection, you can specify the corresponding SonarQube installation name configured in Jenkins
                  sh '${scannerHome}/bin/sonar-scanner'  //mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.11.0.3922:sonar'
                }
            }
        }
    }
}
