pipeline {
  agent {label 'slavesw'}
  stages {
    stage ('my build') {
      steps {
        sh 'mvn package' 
        sh 'whoami'
        sh 'sudo cp -r /home/jenkinsla/workspace/Second pipeline/target/hello-world-war-1.0.0.war /opt/tomcat/apache-tomcat-10.0.27/webapps/'
        sh 'ls'
        sh 'pwd'
      }
    }
    stage ('my deploy') {
      steps { 
        
        sh 'sudo sh /opt/tomcat/apache-tomcat-10.0.27/bin/shutdown.sh'
        sh 'sleep 2'
        sh 'sudo sh /opt/tomcat/apache-tomcat-10.0.27/bin/startup.sh'
      }
    }
  }
}
