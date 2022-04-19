pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-ssh-key', url: 'git@github.com:andovnar2021/php-app.git']]])
                sh 'ls -la'
                withAWS(credentials:'secondcred') {
                    sh 'aws s3 ls'
    // do something
                }
            }
        }
    }
}
