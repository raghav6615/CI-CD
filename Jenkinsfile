pipeline {
	agent any
	tools {
		jdk 'Java_11'
	}
	environment { 
    	dockerImage = ''
		registry = "raghav6615/demo"
		DOCKERHUB_CREDENTIALS=credentials('docker_cred')
    }
	stages {
		stage('build') {
			steps {
			echo 'Building the source'
			bat 'mvn clean compile'
			}
		}
		stage('test') {
			steps {
			echo 'Testing the source'
			bat 'mvn test'
			}
		}
		stage('package') {
			steps {
			echo 'Packaging the source'
			bat 'mvn package'
			}
		}
		stage('Building Our Image') {
			steps {
				script{
					dockerImage=docker.build()
				}
			bat 'docker build . --tag demo'
		}
}
	
	}
}