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

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${ECR_REPO}:${IMAGE_TAG}")
                }
            }
        }

        stage('Push to ECR') {
            steps {
                script {
                    sh '''
                        aws ecr get-login-password --region $AWS_REGION | docker login --username AWS --password-stdin 183295408293.dkr.ecr.us-east-1.amazonaws.com/html-website-shipra
                        docker tag ${ECR_REPO}:${IMAGE_TAG} 183295408293.dkr.ecr.us-east-1.amazonaws.com/html-website-shipra/${ECR_REPO}:${IMAGE_TAG}
                        docker push 183295408293.dkr.ecr.us-east-1.amazonaws.com/html-website-shipra/${ECR_REPO}:${IMAGE_TAG}
                    '''
                }
            }
        }

        stage('Test1') {
            steps {
                echo 'Pipeline started and ran successfully.'
            }
        }


    }
}

