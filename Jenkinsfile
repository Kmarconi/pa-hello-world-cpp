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
		checkout scm
            }
    	}	
        stage('Archivage'){
	    steps {
		
		sh' zip -r ../zipped_file.zip *'
		sh 'mkdir Sauvegarde && cp zipped_file.zip /Sauvegarde'
	    }
	}
    }

    post {
        always {
            archiveArtifacts artifacts: 'main', onlyIfSuccessful: true
        }
    }
}
