pipeline {
    agent { label JDK-17 }
    triggers { pollSCM('* * * * *') }
    stages {
        stage ('vcs') {
            steps {
                git url: 'https://github.com/Bathulaprasanna14/spring-petclinicN.git',
                    branch: 'develop'
            }    
        }
        stage ('build') {
            steps {
            sh 'mvn package'
            }
        }
        
        stage('postbuild') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar',
                                 onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/*.xml'                    
            }
        }                                                   
    }
}