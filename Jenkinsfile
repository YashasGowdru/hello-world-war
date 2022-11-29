pipeline {
  agent any
  stages {
    stage ('Second build') {
      steps {
        sh 'ls'
        sh 'pwd'
        sh 'mvn package'
        sh 'whoami'
      }
    }
    stage ('Deploy') {
      steps {
        sh 'cp -R target/hello-world-war-1.0.0.war /opt/apache-tomcat-10.0.27/webaps/'
        sh 'sudo sh /opt/apache-tomcat-10.0.27/bin/shutdown.sh'
        sh 'sleep 2'
        sh 'sh /opt/apache-tomcat-10.0.27/bin/shutdown.sh'
      }
    }
  }
}
