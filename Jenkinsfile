pipeline{
    agent any

    stages{
        stage('Git check'){
            steps{
                git branch: 'main', url: 'https://github.com/numan05/sample_CICD.git'
            }

        }
        stage('Unit test'){
            steps{
                sh 'mvn test'
            }

        }
    }
}