pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                withCredentials([file(credentialsId: 'PRIVATE_KEY', variable: 'my-public-key')]) {
                   sh 'use $my-public-key'
                }

             }
         }      
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-west-2',credentials:'wach-jenkins-cred') {
                  sh 'echo "Uploading content with AWS creds"'
                   sh "aws s3 cp/index.html s3://jyoti.js"
                  }
              }
         }
     }
}
