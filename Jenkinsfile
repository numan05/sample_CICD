pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('BUILD') {
            steps {
                echo "Building.."
                sh '''
                echo "This is a shell command for building"
                '''
            }
        }
        stage('TEST') {
            steps {
                echo "Testing.."
                sh '''
                echo "A shell command for Testing"
                '''
            }
        }
        stage('DELIVER') {
            steps {
                echo "Deliver.."
                sh '''
                echo "A shell command for delivering"
                '''
            }
        }
    }
}