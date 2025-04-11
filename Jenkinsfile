pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Sleep5+10') {
            steps {
                sleep 5
                sleep 10
            }
        }
        stage('Build') {
            steps {
                bat './mvnw package'
            }
        }
        stage('Test & Cover Results') {
            steps {
                junit '**/target/surefire-reports/*.xml'
                recordCoverage(tools: [[pattern: '**/jacoco.xml']])
            }
        }
        stage('Archive Artifact') {
            steps {
                 archiveArtifacts artifacts: 'target/*.jar'
            }
        }
        stage('Goodbye') {
            steps {
                echo 'Bye World'
            }
        }
    }
}
