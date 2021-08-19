pipeline {
    agent { docker { image 'python:3.7.2' } }
    stages {
        stage('Test') {
            steps {
                sh 'python sample_unit_test.py'
        }
        }
        stage('Deploy') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS' 
              }
            }
            steps {
                echo 'Application deployed'
            }
        }
    }
}