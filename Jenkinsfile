pipeline {
    agent any

    stages {
        stage('Clone-Repo') {
	    	steps {
	        	checkout scm
	    	}
        }
	 stage ('Build'){
	        steps {
			sh 'mvn install -Dmaven.test.skip=true'
                }
	}

	stage('Run Tests') {
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
		sh 'sshpass -p tiwariji scp target/flipkart-1.0-SNAPSHOT.jar tiwariji@172.31.4.197:/home/tiwariji/apache-tomcat-8.5.98/webapps'
	}
    }
}
}
