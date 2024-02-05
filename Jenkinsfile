pipeline {
    agent any

    stages {
        stage('Clone-Repo') {
	    	steps {
	        	checkout scm
	    	}
        }

	stage ('Compile') {
	   steps {
		sh 'mvn clean compile'
	   }
	}
	stage ('Run Tests') {
	    steps {
		sh 'mvn test'
	    }
	}
        stage('Package as WAR') {
            steps {
                sh 'mvn package'
            }
        }
	stage('Deployment') {
	   steps {
		sh 'sshpass -p staragile scp target/gamutkart.war staragile@172.31.36.114:/home/staragile/apache-tomcat-9.0.85/webapps'
	}
    }
}
}
