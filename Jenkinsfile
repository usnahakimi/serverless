pipeline {
    agent { docker { image 'python:3.7.2' } }
    stages {
        stage('Test') {
            steps {
                sh 'python sample_unit_test.py'
        }
        }
        stage('Deploy to S3') {
            steps {
                withAWS(region:'eu-west-2', credentials:'aws-credentials') {
                    s3Upload( 
                        bucket: 'usna-s3', 
                        path: "", // no trailing slash 
                        includePathPattern: "**/*.html",
                        workingDir: "www" 
                    )
                }
            }
        }
    }
}