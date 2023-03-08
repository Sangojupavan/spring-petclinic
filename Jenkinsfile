pipeline{
    agent { label JDK_17 }
    stages {
        stage {
            steps ('vcs_1') {
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