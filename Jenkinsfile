pipeline {
    agent any
    stages {
        stage('Clone sources') {
            steps {
		        checkout scm
            }
        }
        stage('SonarQube analysis') {
            steps {
                // demo step
                sh 'echo Demo step'
                withSonarQubeEnv('SonarQube') {
                    sh "./gradlew sonarqube"
                }
            }
        }
        stage("Quality gate") {
            steps {
                waitForQualityGate abortPipeline: true
            }
        }
    }
}
