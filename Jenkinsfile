properties([ 
pipelineTriggers([pollSCM('H/3 * * * *')]) 
])
node() { 
cleanWs() 
checkout scm 
sh "make" 
sh "./main" 
}
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'make'
            }
        }
	stage('Checkout code') {
            steps {
            	node{
		    checout scm
		}
            }
    	}	
        
    }

    post {
        always {
            archiveArtifacts artifacts: 'main', fingerprint: true
        }
    }
}
