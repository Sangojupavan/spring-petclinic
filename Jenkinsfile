pipeline{
    agent { label JDK_17 }
    stages {
        stage('vcs_1') {
            steps {
                git url: 'https://github.com/Sangojupavan/spring-petclinic.git',
                    branch: 'declarative'
            }
        }
        stage('pacakge') {
            steps {
                sh 'mvn package'
            }
        }
        stage('post build') {
            steps {
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                                 onlyIFSuccessfull: true
                junit testResults: '**/surefire-reports/TEST-*.xml'                 
            }
        }
    }
}