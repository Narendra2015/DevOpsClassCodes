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
               sshagent(['tomcat-dev']) {
                    sh 'ssh -o StrictHostKeyChecking=no target/*.war narendrasagar1993@35.200.222.78:/opt/tomcat/webapps/'
             } 
            }             
         }
     }
   }
