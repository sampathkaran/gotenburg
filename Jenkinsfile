pipeline {
	agent any

	stages {
	    stage('Checkout') {
	        steps {
				checkout scm
			}
		}
		stage('Build') {
	        steps {
				sh '/home/sampath/Distros/apache-maven-3.6.0/bin/mvn install'
	        }
		}
		stage('Deployment') {
			steps {
				sh 'sshpass -p "123" scp target/gamutkart.war sampath@172.17.0.3:/home/sampath/Distros/apache-tomcat-8.5.38/webapps'
				sh 'sshpass -p "123" ssh sampath@172.17.0.3 "JAVA_HOME=/home/sampath/Distros/jdk1.8.0_151" "/home/sampath/Distros/apache-tomcat-8.5.38/bin/startup.sh"'
			}
		}

	}
}
