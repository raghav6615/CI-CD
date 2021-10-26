pipeline {
	agent any
	tools {
		jdk 'Java_11'
	}
	environment { 
    	dockerImage = ''
		registry = "raghav6615/demo:$BUILD_NUMBER"
		registryCredential= 'docker_cred'
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
					dockerImage=docker.build(registry)
				}
			}
		}
		stage('Deploy our image') { 
            steps { 
                script { 
                    docker.withRegistry( '', registryCredential ) { 
                        dockerImage.push() 
                    }
                } 
            }
        } 
		stage('Cleaning up') {
			steps {
				bat "docker rmi $registry"
			}
		}
	}
}
