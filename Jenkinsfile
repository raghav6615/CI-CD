pipeline {
	agent any
	tools {
		jdk 'Java_11'
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
		
	
	}
}