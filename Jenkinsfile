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
        stage ('Upload Jar To Nexus') {
            steps {
                nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'maven-simple', 
                        classifier: '', 
                        file: 'target/Simple-Maven-1.0.0.jar', 
                        type: 'jar'
                    ]
                ], 
                credentialsId: 'nexus3', 
                groupId: 'com.github.jitpack', 
                nexusUrl: '44.205.246.56:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'maven-simple-release', 
                version: '1.0.0'
            }
        }
    }
}