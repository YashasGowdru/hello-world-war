pipeline{
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
  }
}
