pipeline {
    agent { label 'JDK_17' }
    triggers { pollSCM('* * * * *') }
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
          stage('sonar analysis') {
            steps {
                withSonarQubeEnv('SONAR_CLOUD') {
                sh 'mvn clean package sonar:sonar -Dsonar.organization=springpetclinic143'
                }
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