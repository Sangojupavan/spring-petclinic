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
               withSonarQubeEnv(credentialsId: 'a8ca89a1b1a5db556cfbcab04c8ef9cb6dade6c1', installationName: 'SONAR_CLOUD') { // You can override the credential to be used
               sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
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