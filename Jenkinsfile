pipeline{
    agent any
    tools {
        maven 'maven4'
    }
    stages {
        stage ('Build'){
            steps {
                sh script: 'mvn clean package'
            }
        }
    }
}