pipeline{
    agent { JDK_17 }
    satges {
        stage('vcs') {
            steps  {
                git url: 'https://github.com/Sangojupavan/spring-petclinic.git',
                    branch: 'declarative'
            }
        }
        stage('pacakge') {
            steps  {
                sh 'mvn package'
            }
        }
        stage('build') {
            steps  {
                archiveArtifacts artifacts: '**/target/gameoflife.war',                    
                junit testResults: '**/surefire-reports/TEST-*.xml',
                      onlyIFSuccessfull: true                
            }
        }
    }
}