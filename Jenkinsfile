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
                sh './main build'
            }
        }
        
    }

    post {
        always {
            archiveArtifacts artifacts: 'job/TD-Freestyle-Job-SImple-Cpp/ws/main', fingerprint: true
        }
    }
}
