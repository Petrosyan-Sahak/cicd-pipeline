pipeline {
    agent any
    tools { nodejs "node" }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Petrosyan-Sahak/cicd-pipeline'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }

        stage('Docker_Image') {
            steps {
                sh 'docker build -t npmapp:main -f Dockerfile .'
            }
        }

        stage('Deploy_Docker') {
            steps {
                sh 'docker run -d -p 3000:3000 npmapp:main'
            }
        }
    }
}
