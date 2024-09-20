pipeline {
  agent any
  tools {nodejs "node"}

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from GitHub or other VCS
                git branch: 'dev', url: 'https://github.com/Petrosyan-Sahak/cicd-pipeline'
            }
        }
        
        stage('Install Dependencies') {
            steps {
                // Install dependencies (for Node.js apps)
                sh 'npm install'
            }
        }
        
        stage('Build') {
            steps {
                // Build the app (for example, transpile, compile, etc.)
                sh 'npm run build'
            }
        }
        
        stage('Test') {
            steps {
                // Run unit tests
                sh 'npm test'
                sh 'echo "in the dev" '
            }
        }

      stage('Docker_Image') {
            steps {
                // Run unit tests
              script {
                docker.build("npmapp:dev", "Dockerfile")
              }
            }
        }
      stage('Deploy_Docker') {
            steps {
                // Run unit tests
              script {
              docker.image('npmapp:dev').withRun('-p 3001:3000')
              }
            }
        }

    
  }
}
