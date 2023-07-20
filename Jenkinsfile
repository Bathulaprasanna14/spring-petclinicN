pipeline{
    agent { JDK_17 }
    satges {
        stage {
            steps ('vcs') {
                git url: 'https://github.com/Sangojupavan/spring-petclinic.git',
                    branch: 'declarative'
            }
        }
        stage {
            steps ('pacakge') {
                sh 'mvn package'
            }
        }
        stage {
            steps ('post build') {
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                                 onlyIFSuccessfull: true
                junit testResults: '**/surefire-reports/TEST-*.xml'                 
            }
        }
    }
}