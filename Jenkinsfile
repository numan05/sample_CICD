pipeline{
    agent any

    stages{
        stage('Git check'){
            steps{
                git branch: 'main', url: 'https://github.com/numan05/sample_CICD.git'
            }

        }
        stage("test PythonEnv") {
            bat "pytest mytest.py"
            }
        }
    }