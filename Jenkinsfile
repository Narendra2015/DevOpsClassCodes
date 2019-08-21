pipeline{
   agent any
      stages{
        stage ('compile stage'){
         steps{
            withMaven(maven : 'Maven') {
              sh 'mvn compile'
             }
         }
       }
       stage ('Testing stage') {

        steps{
          withMaven(maven : 'Maven'){
           sh 'mvn test'
          }
         }
        }
          stage ('deployment stage') {
           steps{
            withMaven(maven : 'Maven'){
             sh 'mvn package'
          }
         }
        }
           stage ('deploy to tomcat') {
              steps{
               sshagent(['tomcat-prod']) {
                    sh 'scp -o StrictHostKeyChecking=no target/*.war narendrasagar1993@10.160.0.2:/opt/apache-tomcat-7.0.94/webapps/'
                 }
            }             
         }
     }
   }
