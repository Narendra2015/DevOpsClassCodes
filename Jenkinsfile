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
            sh 'cp target/*.war /opt/apache-tomcat-7.0.94/webapps/'
       }             

     }
   }
