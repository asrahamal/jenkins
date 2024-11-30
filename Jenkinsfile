pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/asrahamal/jenkins.git'
        GIT_BRANCH = 'main'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: "${GIT_BRANCH}", url: "${GIT_REPO}"
            }
        }

        // stage('Install Dependencies') {
        //     steps {
        //         sh 'npm install'
        //     }
        // }

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

        stage('Deploy') {
            steps {
                sh 'docker-compose up -d'
            }
        }
        stage('Check Node and npm') {
    steps {
        sh 'node -v'
        sh 'npm -v'
    }
}

    }

    post {
        always {
            echo 'Cleaning up...'
        }

        success {
            echo 'Build and deploy successful!'
        }

        failure {
            echo 'Build or deployment failed!'
        }
    }
}
