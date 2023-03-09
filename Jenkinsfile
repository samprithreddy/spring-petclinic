pipeline {
    agent {label 'jdk_8'}
    tools {
        jdk 'java 8'
    }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/samprithreddy/spring-petclinic.git',
                     branch: 'declarative'
            
            }
        } 
        stage('package') {
            steps {
                 sh 'mvn verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.projectKey=sampreeth_rahul '
            }
        }
    }
}