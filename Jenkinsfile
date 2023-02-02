pipeline {
     agent any
     stages {
         stage('Build') {
             steps {
                withCredentials([file(credentialsId: '$deploy_to', keyFileVariable: 'keyFile', variable: 'APP_ENV')]) {
                    sh "rm -rf /var/lib/jenkins/workspace/sds/.env"
                     sh "cp -r \$APP_ENV /var/lib/jenkins/workspace/sds/.env"
                }

             }
         }      
         stage('Upload to AWS') {
              steps {
                  withAWS(region:'us-west-2',credentials:'release') {
                  sh 'echo "Uploading content with AWS creds"'
                   sh "aws s3 cp/index.html s3://jyoti.js"
                  }
              }
         }
     }
}
