pipeline {
    agent {label 'jdk_8'}
    parameters {
        choice(name: 'MAVEN_GOAL', choices: ['package', 'install', 'clean'], description: 'Maven Goal')
    }
    stages {
        stage('vcs') {
            steps {
                git url: 'https://github.com/samprithreddy/spring-petclinic.git',
                     branch: 'declarative'     
            }
        } 
        stage('package') {
            tools {
                jdk 'JDK_17'
            }
            sh "mvn ${params.MAVEN_GOAL}"
        stage('sonar analysis') {
            steps {
                // performing sonarqube analysis with "withSonarQubeENV(<Name of Server configured in Jenkins>)"
                withSonarQubeEnv('SONAR_CLOUD') {
                    sh 'mvn verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.projectKey=sampreeth_rahul -Dsonar.organisationKey=sampreeth'
                }
            }
        }
        }
    }
}