pipeline {
    agent { label 'JDK_17' }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/Sangojupavan/spring-petclinic.git',
                    branch: 'declarative'
            }
        }
        stage('pacakge_1') {
            steps {
                sh 'mvn package'
            }
        }
        stage('build') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar',
                                 onlyIfSuccessful: true
                junit testResults: '**/surefire-reports/*.xml'                    
                                                 
            }
        }
    }
}