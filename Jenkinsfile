pipeline {
    agent {
        node {
            label 'maven'
        }
    }
    
    stages {
        stage('Clone-code') {
            steps {
                git branch: 'main', url: 'https://github.com/mooa2023/tweet-trend-new.git'
            }
        }
    }
}