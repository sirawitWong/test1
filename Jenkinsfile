pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/sirawitWong/test1.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh '/usr/local/bin/docker build -t my-web-cicd .'
            }
        }
        stage('Run Container') {
            steps {
                sh '/usr/local/bin/docker rm -f my-web || true'
                sh '/usr/local/bin/docker run -d --name my-web -p 9090:80 my-web-cicd'
            }
        }
    }
}

