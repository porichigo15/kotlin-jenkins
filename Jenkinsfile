pipeline {
    agent any

    stages {
        stage('Clean') {
            steps {
                sh 'chmod +x ./gradlew'
                sh './gradlew clean'
            }
        }
        stage('Build') {
            steps {
                sh 'chmod +x ./gradlew'
                sh './gradlew assembleDebug'
            }
        }
        stage('Test') {
            steps {
                sh 'chmod +x ./gradlew'
                sh './gradlew test --stacktrace'
            }
        }
    }

    triggers {
        pollSCM('* * * * *')
    }

    post {
        success {
            notify("success")
        }
        failure {
            notify("failure")
        }
    }
}

def notify(status) {
    sh "${status}"
}