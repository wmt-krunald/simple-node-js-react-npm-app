pipeline {
    agent any
 
    tools {nodejs "node"}

    environment {
        CI = 'true'
    }

    stages{

        stage('check') {
            steps {
            sh 'npm config ls'
            }
        }

        stage('build') {
            steps {
                sh 'npm i'
                sh 'npm run build'
            }
        }

        stage('deploy') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Finished using the web site? (Click "Proceed" to continue)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }

}