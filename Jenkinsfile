pipeline {
    agent any

    environment {
        VERCEL_TOKEN = credentials('vercel_token')
    }

    stages {
        stage('Install') {
            steps {
                bat 'npm ci'
            }
        }
        stage('Test') {
            steps {
                echo 'Skipping tests - no test script found'
            }
        }
        stage('Build') {
            steps {
                bat 'npm run build'
            }
        }
        stage('Deploy') {
            steps {
                bat 'npx vercel --prod --yes --token=%VERCEL_TOKEN%'
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Pipeline failed! Check logs.'
        }
    }
}