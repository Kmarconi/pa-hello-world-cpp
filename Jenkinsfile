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
		archiveArtifacts artifacts: 'main', onlyIfSuccessful: true
		sh 'tar -zcvf Sauvegarde.tar.gz .'
	    }
	}
    }

    post {
        always {
            sh 'echo True'
        }
    }
}
