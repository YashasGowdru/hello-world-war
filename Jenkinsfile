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
        sh 'whoami'
        sh 'ls'
        sh 'pwd'
      }
    }
  }
}
