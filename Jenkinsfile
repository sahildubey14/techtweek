pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                withCredentials([file(credentialsId: 'PRIVATE_KEY', keyFileVariable: 'keyFile', variable: 'APP_URL')]) {
                   sh "cp \$APP_URL /var/lib/jenkins/workspace/sds/.env"
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
