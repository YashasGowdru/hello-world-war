pipeline {
  agent {label 'build_slave1'}
  stages {
    stage ('my build') {
      steps {
        sh 'mvn package' 
        sh 'whoami'
        sh 'ls'
        sh 'pwd'
      }
    }
    stage ('my deploy') {
      steps { 
        sh 'sudo cp -r target/hello-world-war-1.0.0.war /opt/tomcat/apache-tomcat-10.0.27/webapps/'
        sh 'sudo sh /opt/tomcat/apache-tomcat-10.0.27/bin/shutdown.sh'
        sh 'sleep 2'
        sh 'sudo sh /opt/tomcat/apache-tomcat-10.0.27/bin/shutdown.sh'
      }
    }
  }
}
