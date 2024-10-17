pipeline {
    agent {
        node {
            label 'docker-agent-python'
        }
        
    }
    #environment {    SHELL = '/bin/bash' }
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
                script {
                    sh '''
                    pwd
                    #java -Dorg.jenkinsci.plugins.durabletask.BourneShellScript.LAUNCH_DIAGNOSTICS=true -jar
                    #jenkins.war
                    #pip install -r requirements.txt
                    #dir('/home/jenkins/.local/bin/')
                    #pip install coverage
                    #pip install pytest
                    #coverage run -m pytest
                    #coverage xml #> /home/jenkins/workspace/quality/cover
                    #echo "Build block is executed"
                '''
                }
            }
        }
        stage('TEST') {
            steps {
                echo "Testing.."
                sh '''
                #cd myapp
                python3 hello_world.py
                #python3 randomnum.py --name=Numan
                '''
            }
        }
        stage('CODE ANALYSIS') {
            steps {
                script {
                    withSonarQubeEnv(installationName: 'SonarQubeServer', credentialsId: 'sonar-api-key') {
                    sh '''
                    echo "Touching sonarqube"
                    #sonar-scanner
                    '''
                }
                }
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