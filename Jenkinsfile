pipeline {
    agent any
    options {
        skipDefaultCheckout(true) // skip the default checkout
    }


    stages {

        stage('clean up code ') {
            steps {
                cleanWs()
            }
        }

        stage('checkout using SCM') {
            steps{
                checkout scm   // checkout the code 
            }
        }


        stage('Build') {
            agent {
                docker {
                    image 'node:18-alpine'
                    args '-u root'
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
                    // sh 'chown -R 992:992 "/ .npm"'

                    sh 'npm install'
                    sh 'npm run build'
                    
                    // Show the final state of files after build
                    sh 'ls -l'
                }
            }
        }
    }
}
