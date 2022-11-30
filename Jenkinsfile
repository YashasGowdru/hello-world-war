pipeline {
	agent none
        stages {
           stage ("tomcat build & move to other node") {
	      agent {label "build_slave1"}
              steps {
		      sh 'ls'
                      sh 'pwd'
                      sh 'mvn package'
		      sh 'chmod 777 target'
		      sh 'scp -R target/hello-world-war-1.0.0.war jenkinsla@172.31.45.23:/opt/tomcat/webapps'
		      sh 'echo "sucessfully copied build to other node"'
              }
	    }
	   stage ('diploy in node2') {
	   	agent {label "slavesw"}
              	steps {
		  	sh 'sudo sh /opt/tomcat/bin/shutdown.sh'                   
                  	sh 'sudo sleep 3'
                  	sh 'sudo sh /opt/tomcat/bin/startup.sh'
                  	echo "diployment is sucessfull"
                  	echo "copy the public ip of instace and open it in browser with port:8090"
		}
	   } 	   
      }
}
