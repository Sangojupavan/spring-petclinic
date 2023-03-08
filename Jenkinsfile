pipeline{
    agent { label 'JDK_17' }
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
        
    }
}