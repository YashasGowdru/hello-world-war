pipeline {
    agent {label 'slave1'}
    stages {
        stage('my Build') {
            steps {
                sh 'docker build -t tomcat_build:latest .' 
            }
        }  
        stage('publish stage') {
            steps {
                sh "echo ${BUILD_NUMBER}"
                sh 'docker login -u yashas1234 -p Yashas@123'
                sh 'docker tag tomcat_build:latest yashas1234/yashasdock:latest'
                sh 'docker push yashas1234/yashasdock:latest'
            }
        } 
        stage( 'my deploy' ) {
        agent {label 'slave2'} 
            steps {
               sh 'docker pull yashas1234/yashasdock:latest'
               sh 'docker rm -f yashasdock'
               sh 'docker run -d -p 8080:8080 --name yashasdock yashas1234/yashasdock:latest'
            }
        }    
    } 
}
