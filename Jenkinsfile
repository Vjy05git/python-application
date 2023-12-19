pipeline {
    agent { label 'ec2' }
   stages { 
    

        stage('Build2') {
            steps {
                sh 'docker build -t vjypy1 .'

                sh 'docker run -d -it --name vjypy1 -p8000:3000 vjypy1'

                 }
        }

          }

}
