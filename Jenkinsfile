pipeline {
	agent none
        stages {
           stage ("tomcat build & move to other node") {
	      agent {label "build_slave1"}
              steps {
		      sh 'ls'
                      sh 'pwd'
		      sh 'echo $(BUILD_NUMBER)'
                      sh 'mvn deploy'
		      sh 'pwd'
		      sh 'echo "sucessfully copied build to other node"'
              }
	    }
	   stage ('diploy in node2') {
	   	agent {label "slavesw"}
              	steps {
		  	sh 'pwd'
			sh 'whoami'
			sh 'curl -u yashasjgowda@gmail.com:Devops@123 -O https://yashasjfrog.jfrog.io/artifactory/libs-release-local/com/efsavage/hello-world-war/$(BUILD_NUMBER)/hello-world-war-$(BUILD_NUMBER).war'		
			sh 'sudo cp -R hello-world-war/$(BUILD_NUMBER).war /opt/tomcat/webapps'
			sh 'sudo sh /opt/tomcat/bin/shutdown.sh'                   
                  	sh 'sudo sleep 3'
                  	sh 'sudo sh /opt/tomcat/bin/startup.sh'
                  	echo "diployment is sucessfull"
                  	echo "copy the public ip of instace and open it in browser with port:8090"
		}
	   } 	   
      }
}
