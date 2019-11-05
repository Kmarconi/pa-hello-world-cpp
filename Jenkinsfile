properties([ 
pipelineTriggers([pollSCM('H/3 * * * *')]) 
])
node() { 
cleanWs() 
checkout scm 
sh "make" 
sh "./main" 
}
node {   
    stage('Build') {
        sh 'make'
    }
    stage('Checkout code') {
	checkout scm
    }	
    stage('Archivage'){
	steps{
	     archiveArtifacts artifacts: 'main', onlyIfSuccessful: true
	}
    }
}
