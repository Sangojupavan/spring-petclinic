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
                sh 'mvn clean verify sonar:sonar -Dsonar.organization=springpetclinic143 -Dsonar.login=2f9590ad4f09dd82feb0e369b767e73e39a06d69'
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