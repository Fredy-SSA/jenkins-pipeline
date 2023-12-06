pipeline {
    agent {
        docker {
            image 'node:latest'
            args '--rm -it --name myapp -p 3000:3000'

        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
                
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'

                sh 'hostname'
                sh 'ls -lah'

             
                
                
                
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
