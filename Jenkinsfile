pipeline {
    agent {
      label  'Slave'
    }
    tools {
        maven 'M2_HOME'
    }
    stages {
        stage('checkout the project') {
            steps {
                git branch: 'main', url: 'https://github.com/shashikrpet/java-maven-pipeline-jenkins.git'
            }
        }
        stage('Build the Package') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deploy on  Slaves') {
            steps {
                  deploy adapters: [tomcat9(credentialsId: '71b0d510-026e-43d2-995b-556a0efeb7b9', path: '', url: 'http://3.110.175.13:8081/')], contextPath: 'Slave', onFailure: false, war: '**/*.war'
                }
        }
    }
}
