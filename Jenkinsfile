pipeline {
    agent { label 'ec2' }
   stages { 
    stage('Build') {
            steps {
               
                sh 'sudo apt install git -y'
                sh 'git clone https://github.com/Vjy05git/python-application.git'

                 }
        }

        stage('Build2') {
            steps {
                sh 'docker build -t vjypy1 .'

                sh 'docker run -d -it --name vjypy1 -p8000:3000 vjypy1'

                 }
        }

          }

}
