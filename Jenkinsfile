pipeline{
    agent any
    tools {
        maven 'maven5'
    }
    stages {
        stage ('Build'){
            steps {
                sh script: 'mvn clean package'
            }
        }
    }
}