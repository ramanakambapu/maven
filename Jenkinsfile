pipeline {
	agent any
	
	stages {
		stage ('Compile Stage') {
			steps {
				withMaven(maven : 'apache-maven-3.5.0'){
					sh 'mvn clean compile'
				}
			}
		}

		stage ('Testing Stage') {
			steps {
				withMaven(maven : 'apache-maven-3.5.0'){
					sh 'mvn test'
				}
			}
		}
		stage ('Installing Stage') {
			steps {
				withMaven(maven : 'apache-maven-3.5.0'){
					sh 'mvn install'
				}
			}				
		}	
		stage ('Deployment Stage') {
			steps {
				withMaven(maven : 'apache-maven-3.5.0'){
					sh 'mvn deploy'
				}
			}				
		}

	post {
        	always {
	            echo 'One way or another, I have finished'
	            deleteDir() /* clean up our workspace */
	        }
	        success {
	            echo 'I succeeeded!'
	        }
	        unstable {
	            echo 'I am unstable :/'
	        }
	        failure {
	            echo 'I failed :('
	        }
	        changed {
	            echo 'Things were different before...'
	        }

	}
}
