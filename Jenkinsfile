pipeline {
    agent {
        node {
            label 'docker-agent-python'
        }
    }
    tools {
        maven 'Maven 3.6.3' // Use the name of your Maven installation
    }
    environment {
        PATH = "${env.PATH}:/home/jenkins/.local/bin:/path/to/maven/bin"
    }
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('BUILD') {
            steps {
                echo "Building.."
                script {
                    sh '''
                    pwd
                    #java -Dorg.jenkinsci.plugins.durabletask.BourneShellScript.LAUNCH_DIAGNOSTICS=true -jar
                    #jenkins.war
                    #pip install -r requirements.txt
                    #dir('/var/lib/jenkins/workspace/my-python-test')
                    #cd /var/lib/jenkins/workspace/my-python-test
                    #pwd
                    #pip install coverage
                    #pip install pytest
                    #coverage run -m pytest
                    #coverage xml #> /home/jenkins/workspace/quality/cover
                    echo "Build block is executed"
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
                    echo "Touching sonarqube but not able to run the analysis yet!"
                    mvn clean package sonar:sonar
                    #sonar-scanner
                    '''
                    }
                }
            }
        }
        stage("Quality Gate"){
            steps {
                script {
                    timeout(time: 1, unit: 'HOURS') {
                    def qg = waitForQualityGate()
                        if (qg.status != 'OK') {
                            error "Pipeline aborted due to quality gate failure: ${qg.status}"                 
                        }
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