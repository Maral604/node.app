pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git credentialsId: 'github-token', url: 'https://github.com/Maral604/node-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t node-app .'
            }
        }

        stage('Docker Run') {
            steps {
                sh 'docker rm -f my-node-app || true'
                sh 'docker run -d -p 3000:3000 --name my-node-app node-app'
            }
        }
    }
}

