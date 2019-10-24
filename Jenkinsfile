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
		
		sh 'tar -zcvf Sauvegarde.tar.gz .'
		sh 'mkdir Sauvegarde && cp Sauvegarde.tar.gz /Sauvegarde'
	    }
	}
    }

    post {
        always {
            archiveArtifacts artifacts: 'main', onlyIfSuccessful: true
        }
    }
}
