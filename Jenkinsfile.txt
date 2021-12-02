pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'github_credentials', url: 'https://github.com/praveengopala/First_Repo.git']]])
            }
        }
        stage('build') {
            steps {
                git credentialsId: 'github_credentials', url: 'https://github.com/praveengopala/First_Repo.git'
                bat 'python program1.py'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing in Progress'
                echo 'Testing completed'
                
            }
        }
    }
}
