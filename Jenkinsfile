pipeline {
    agent any

    environment {
        AWS_REGION = 'us-east-1'
        ECR_REPO = 'html-website-shipra'
        IMAGE_TAG = "${BUILD_NUMBER}"
        AWS_ACCESS_KEY_ID = credentials('aws-access-key')
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret-key')
        AWS_DEFAULT_REGION = "us-east-1"
        AWS_ACCOUNT_ID = '183295408293'
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
        

        stage('Debug AWS Creds') {
            steps {
                sh '''
                echo "Access Key: $AWS_ACCESS_KEY_ID"
                echo "Secret Key: $(echo $AWS_SECRET_ACCESS_KEY | cut -c1-4)****"
                aws sts get-caller-identity
                '''
            }
            }

               stage('Push to ECR') {
            steps {
                script {
                    sh '''
                        echo "🔐 Logging in to ECR..."
                        aws ecr get-login-password --region $AWS_DEFAULT_REGION | \
                        docker login --username AWS --password-stdin $AWS_ACCOUNT_ID.dkr.ecr.$AWS_DEFAULT_REGION.amazonaws.com
                    '''
                    // Tag and push using dockerImage object
                    dockerImage.tag("${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${ECR_REPO}", IMAGE_TAG)
                    dockerImage.push(IMAGE_TAG)
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

