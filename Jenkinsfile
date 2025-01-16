pipeline {
    agent any
    stages {
        stage('build') {
            docker {
                image 'node:1818-alpine'
                reuseNode true // Reuse the node for the next stages
            }
        }
        steps {
            sh '''
                ls -l
                node --version
                npm --version
                npm install
                npm run build
                ls -l
            '''
        }
    }
}