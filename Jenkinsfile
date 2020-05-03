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
}
}
