pipeline
{
agent any
stages
{
  stage ('scm checkout') {
    steps {
            git branch: 'master', url: 'https://github.com/patelsandeep6/maven-project'
        }
}
  stage('compile source code')
{ 
    steps {
             withMaven(jdk: 'localjdk-8', maven: 'localmaven') {
             sh 'mvn compile'
          }
       }
   }
   stage ('test') {
       steps {
           withMaven(jdk: 'localjdk-8', maven: 'localmaven') {
           sh 'mvn test'
}
       }
   }
  
  stage ('build my job')
    {
        steps {
            withMaven(jdk: 'localjdk-8', maven: 'localmaven') {
                sh 'mvn package'
            }
        }
    }
  stage('tomcar dev deployment'){
       steps{
         sshagent(['deploytomcat']) {
           sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.28.230:/var/lib/tomcat7/webapps'
             }
       }
   }
}
}
