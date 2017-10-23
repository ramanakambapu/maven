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
	}
	post {
	    failure {
	        mail to: 'kotharakesh12@gmail.com',
	             subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
	             body: "Something is wrong with ${env.BUILD_URL}"
    		    }
	      }

	
}
