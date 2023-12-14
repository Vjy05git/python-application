Jenkinsfile to deploy app in aws ec2


Jenkinsfile

pipeline {
    agent any

    environment {
        duser = credentials(vjyguvi).username
        dpass = credentials(dckr_pat_zUSMCYxBddrKWv1C92ARjVudXOg).password
        EC2_INSTANCE_IP = 3.110.197.41
        EC2_PEM_KEY = credentials(ec2pem)

    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Vjy05git/python-application.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker image
                    sh "docker build -t ${duser}/your-web-app:${env.BUILD_NUMBER} ."
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    // Push Docker image to Docker Hub
                    sh "docker login -u ${duser} -p ${dpass}"
                    sh "docker push ${duser}/your-web-app:${env.BUILD_NUMBER}"
                    sh "docker logout"
                }
            }
        }

        stage('Deploy to AWS EC2') {
            steps {
                script {
                    // Copy the Docker image to EC2 instance
                    sh "scp -o StrictHostKeyChecking=no -i ${EC2_PEM_KEY} target/docker/your-web-app.tar ec2-user@${EC2_INSTANCE_IP}:/path/on/ec2/"

                    // SSH into EC2 instance and run the Docker container
                   sh "ssh -o StrictHostKeyChecking=no -i ${EC2_PEM_KEY} ec2-user@${EC2_INSTANCE_IP} 'docker run -d -p 80:80 your-web-app'"
                }
            }
        }
    }
}
