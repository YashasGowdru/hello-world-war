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
        sh 'sudo cp -R target/hello-world-war-1.0.0.war /opt/apache-tomcat-10.0.27/webapps/'
        sh 'ls'
        sh 'pwd'
      }
    }
  }
}
