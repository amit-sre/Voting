pipeline {
    agent any

    stages {
        stage('checkout') {
            steps {
                //git branch: 'main', url: 'https://github.com/amit-sre/Voting/tree/main/vote'
                withCredentials([string(credentialsId: 'github-cred', variable: 'GITHUB_TOKEN')]) {
                    sh 'curl -H "Authorization: token $GITHUB_TOKEN" https://api.github.com/repos/amit-sre/Voting/contents/vote'
                }
                // Add your build commands here
            }
        }
        stage('Build') {
            steps {
                sudo docker build -t voting-app .
                echo 'Building the application...'
                // Add your test commands here
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Add your deployment commands here
            }
        }
    }

    post {
        always {
            echo 'This will always run after the pipeline completes.'
        }
        success {
            echo 'This will run only if the pipeline succeeds.'
        }
        failure {
            echo 'This will run only if the pipeline fails.'
        }
    }
}