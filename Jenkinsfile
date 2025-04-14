pipeline {
    agent any

    environment {
        AWS_REGION = 'us-east-1'
        ECR_REPO = 'html-website-shipra'
        IMAGE_TAG = "${BUILD_NUMBER}"
    }

    stages {
        stage('Test') {
            steps {
                echo 'Pipeline started and ran successfully.'
            }
        }

        stage('Checkout') {
            steps {
                git(
                    url: 'https://github.com/goshipra/MyPersonalWebsite.git',
                    branch: 'main',
                    credentialsId: 'github-credentials1'
                )
            }
        }

        stage('Test1') {
            steps {
                echo 'Pipeline started and ran successfully.'
            }
        }


    }
}

