pipeline {
    environment {
	register = "dzbeda/test"
	dockerImage = " "
	registryCredential ="9479ace2-d10f-49a7-96ab-06378e89d204"
	}
	agent any
	//{ label 'mfd-build-5' }

    stages {
        stage('Connect to git') {
            steps {
                    git branch: 'main', credentialsId: '16c99938-b8f3-4394-89e3-10883a65c0c3', url: 'https://github.com/dzbeda/test.git'
			}
        }
		stage ('Build docker image') {
            steps{
                script {
				dockerImage = docker.build register + ":$BUILD_NUMBER"
                }
            }
       }
	   	stage ('Docker Image push') {
		    steps {
				script {
				    docker.withRegistry( '', registryCredential ) {
					dockerImage.push()
					}
				}
				
			}
        }
   }
}
