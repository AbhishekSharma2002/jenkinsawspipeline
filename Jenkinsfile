pipeline {
    agent any
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true // Reuse the node for the next stages
                }
            }
            steps {
                script {
                    // Show the initial state of files
                    sh 'ls -l'
                    
                    // Show Node.js and npm versions
                    sh 'node --version'
                    sh 'npm --version'
                    
                    // Install dependencies and run build
                    sh 'npm install'
                    sh 'npm run build'
                    
                    // Show the final state of files after build
                    sh 'ls -l'
                }
            }
        }
    }
}
