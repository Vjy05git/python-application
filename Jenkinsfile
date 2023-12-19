pipeline {
    agent { ec2 }
    stages {
        stage('Build') {
            steps {
                git 'https://github.com/Vjy05git/python-application.git'

                 }
        }

        stage('Build') {
            steps {
                sh 'docker build -t vjypy .'

                sh 'docker run -d -it --name vjypy -p8000:8000 vjypy'

                 }
        }

         }
    }

