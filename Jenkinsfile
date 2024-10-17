pipeline {
    agent any

    triggers {
        cron('H/10 * * * 1') // Triggers every 10 minutes on Mondays
    }

    stages {
        stage('Build & Test') {
            steps {
                script {
                    // Run the build and tests using Maven
                    sh 'mvn clean verify'
                }
            }
        }
        stage('Code Coverage') {
            steps {
                script {
                    // Generate code coverage report using JaCoCo
                    sh 'mvn jacoco:report'
                }
            }
        }
    }

    post {
        always {
            // Archive the Jacoco report
            archiveArtifacts artifacts: '**/target/site/jacoco/**/*', allowEmptyArchive: true
        }
    }
}

