pipeline {
    agent { label 'ec2' }
   stages { 
    stage('Build') {
            steps {
               
                sh 'sudo apt install git -y'
                git 'https://github.com/Vjy05git/python-application.git'

                 }
        }

        stage('Build2') {
            steps {
                sh 'docker build -t vjypy .'

                sh 'docker run -d -it --name vjypy -p8000:8000 vjypy'

                 }
        }

          }

}
