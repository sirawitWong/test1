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
				sh 'export PATH=/opt/homebrew/bin:/usr/local/bin:$PATH && docker build -t my-web-cicd .'
            }
        }
        stage('Run Container') {
            steps {
		export PATH=/opt/homebrew/bin:/usr/local/bin:$PATH
                sh 'docker rm -f my-web || true'
                sh 'docker run -d --name my-web -p 9090:80 my-web-cicd'
            }
        }
    }
}

