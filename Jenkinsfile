pipeline {
    agent {
        node {
            label 'docker-agent-python'
        }
    }
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('GIT CHECK') {
            steps {
                git branch: 'main', url: 'https://github.com/numan05/sample_CICD.git'
            }
        }
        stage('BUILD') {
            steps {
                echo "Building.."
                sh '''
                cd myapp
                pip install -r requirements.txt
                '''
            }
        }
        stage('TEST') {
            steps {
                echo "Testing.."
                sh '''
                cd myapp
                python3 randomnum.py
                python3 randomnum.py --name=Numan
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
        stage('CODE ANALYSIS') {
            steps {
                withSonarQubeEnv(credentialsId: 'sonar-api-key') {
                sh '''
                echo "Touching sonarqube"
                '''
                }
            }
        }
    }
}