pipeline {
    agent {
        docker {
            image 'node:20'  // Node.js + npm preinstalled
            args '-u root:root' // optional, to avoid permission issues
        }
    }
    environment {
        FIREBASE_DEPLOY_TOKEN = credentials('firebase-token')
    }

    stages {
        stage('Building') {
            steps {
                echo 'Building...'
                sh 'npm install -g firebase-tools'
            }
        }

        stage('Staging Environment') {
            steps {
                echo 'Deploying to Staging Environment...'
                sh "firebase deploy -P fir-29310 --token ${FIREBASE_DEPLOY_TOKEN}"
            }
        }
    }
}
