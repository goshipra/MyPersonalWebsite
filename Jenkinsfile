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
                git 'https://github.com/goshipra/MyPersonalWebsite.git'
            }
        }

        stage('Test') {
            steps {
                echo 'Pipeline started and ran successfully.'
            }
        }


    }
}

