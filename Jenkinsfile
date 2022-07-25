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
                script {
                    def mavenPom = readMavenPom file: 'pom.xml'
                    def nexusRepoName = mavenPom.version.endwith ("SNAPSHOT") ? "maven-simple-snapshot" : "maven-simple-release"
                    // def version() {
                    //     def matcher = readFile ('pom.xml') =~ '<version> (.+)</version>'
                    //     matcher ? matcher[0][1] : null
                    // }
                    nexusArtifactUploader artifacts: [
                      [
                            artifactId: 'maven-simple', 
                            classifier: '', 
                            file: "target/maven-simple-${mavenPom.version}.jar", 
                            type: 'jar'
                      ]
                ], 
                credentialsId: 'nexus3', 
                groupId: 'com.github.jitpack', 
                nexusUrl: '44.205.246.56:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: nexusRepoName, 
                version: "${mavenPom.version}"
                    }

                 }
        }
    }
}