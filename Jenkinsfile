pipeline {
    agent { docker { image 'python:3.7.2' } }
    stages {
        stage('test') {
            steps {
                sh 'python sample_unit_test.py'
        }
        }
        stage('deploy') {
            steps {
                withAWS(region:'eu-west-2',credentials:'iam-credentials') {
                    s3Delete(bucket: 'usna-s3', path:'**/*')
                    s3Upload(bucket: 'usna-s3', workingDir:'build', includePathPattern:'**/*');
                }
            }
        }
    }
}