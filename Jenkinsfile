pipeline {
    agent {label 'slave1'}
    stages {
        stage('my Build') {
            steps {
                sh "echo ${BUILD_VERSION}"
                sh 'docker build -t tomcat_build:${BUILD_VERSION} --build-arg BUILD_VERSION=${BUILD_VERSION} .' 
            }
        }  
        stage('publish stage') {
            steps {
                sh "echo ${BUILD_NUMBER}"
                withCredentials([usernamePassword(credentialsId: 'Dockerhub', passwordVariable: 'DockerhubPassword', usernameVariable: 'DockerhubUser')])
                sh 'docker login -u ${env.DockerhubUser} -p ${env.DockerhubPassword}'
                sh 'docker tag tomcat_build:${BUILD_VERSION} yashas1234/yashasdock:${BUILD_VERSION}'
                sh 'docker push yashas1234/yashasdock:${BUILD_VERSION}'
            }
        } 
        stage( 'my deploy' ) {
        agent {label 'slave2'} 
            steps {
               sh 'docker pull yashas1234/yashasdock:${BUILD_VERSION}'
               sh 'docker rm -f yashasdock'
               sh 'docker run -d -p 8080:8080 --name yashasdock yashas1234/yashasdock:${BUILD_VERSION}'
            }
        }    
    } 
}
