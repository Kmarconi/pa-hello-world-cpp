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
		sh 'mkdir Sauvegarde'
		sh 'echo "artifact file" > main.cpp'
	    }
	}
    }

    post {
        always {
            archiveArtifacts artifacts: 'main', onlyIfSuccessful: true
        }
    }
}
